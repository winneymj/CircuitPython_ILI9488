Introduction
============

displayio driver for ILI9488 TFT-LCD displays.

Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://github.com/adafruit/Adafruit_CircuitPython_Bundle>`_.

Usage Example
=============

.. code-block:: python

    import board
    import displayio
    import adafruit_ili9488

    spi = board.SPI()
    tft_cs = board.D9
    tft_dc = board.D10

    displayio.release_displays()
    display_bus = displayio.FourWire(spi, command=tft_dc, chip_select=tft_cs)

    display = adafruit_ili9488.ILI9488(display_bus, width=320, height=480)

    # Make the display context
    splash = displayio.Group()
    display.show(splash)

    color_bitmap = displayio.Bitmap(320, 480, 1)
    color_palette = displayio.Palette(1)
    color_palette[0] = 0xFF0000

    bg_sprite = displayio.TileGrid(color_bitmap,
                                   pixel_shader=color_palette,
                                   x=0, y=0)
    splash.append(bg_sprite)

    while True:
        pass

Documentation
=============

API documentation for this library can be found on `Read the Docs <https://docs.circuitpython.org/projects/ili9341/en/latest/>`_.

For information on building library documentation, please check out `this guide <https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/sharing-our-docs-on-readthedocs#sphinx-5-1>`_.

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_ILI9488/blob/main/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.
