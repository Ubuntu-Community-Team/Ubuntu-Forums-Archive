---
title: "Tif images"
date: 2009-01-21
forum: Multimedia Software
---

### Post by adamsnative on 2009-01-21
can u help me
how many bits are used to represent tif images in gray scale

---

### Post by mcduck on 2009-01-21
Tiff is a rather annoying file format as it's not clearly defined, can contain many different types of data, use many different compression algorithms, might even include several JPG images, vector data, multiple pages and so on. Not to mention that TIFF can also use CMYK colors used in prints, which would mean having 4 color channels as opposed to normal 3. And tiff supports both 8- and 16-bit color channels..

Anyway, in most cases tiff files contain either uncompressed CMYK data (32 bits) or uncompressed RGB data (24 bits), both formats using 8 bits per color channel.

That would still leave you with the option of your black&white image having 8, 24 or 32 bits of data per pixel..

If I'd have to bet on one option, I'd say it's an RGB image with 24 bits per pixel.

---

### Post by automaton26 on 2009-01-21
There are several possibilities - for example, it could be an 8 BitsPerPixel image, with an associated greyscale palette containing 256 colors [ from black {0,0,0} up to white {255,255,255} ]. Each 8-bit value (0-255) would then simply represent the index of the actual color from the palette.

Ultimately it depends on what software/code is used to create the image - I think many medical applications (DICOM?) use 16-bit greyscale, which gives 256*256=65536 shades of grey per-pixel, rather than just 256 as I mentioned in the example above.

---

