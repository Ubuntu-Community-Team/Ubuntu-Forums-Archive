---
title: "[libpng?] Critical error «PNG: Decompression Error»"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Nemo_bis on 2010-02-09
I've scanned a document with OmniPage on a Windows PC; I've saved the images as black and white png and I can open them on Windows, but on Ubuntu Eye of GNOME gives me (for one image only) the critical error «PNG: Decompression Error» and doesn't open it, while Mirage, GIMP, GQview and F-Spot show an empty image. 
The output of a pngcheck -vtf (as suggested [here]("http://osdir.com/ml/graphics.png.devel/2007-03/msg00039.html")) follows:
> File: [...] (101408 bytes)
  chunk IHDR at offset 0x0000c, length 13
    2480 x 3507 image, 1-bit grayscale, non-interlaced
  chunk tEXt at offset 0x00025, length 13, keyword: Software
    none
  chunk pHYs at offset 0x0003e, length 9: 11811x11811 pixels/meter (300 dpi)
  chunk IDAT at offset 0x00053, length 8192
    zlib: deflated, 32K window, default compression
    zlib: inflate error = -3 (data error)
  Chunk name 00 00 20 00 doesn't conform to naming rules.
  chunk  at offset 0x0205b, length -1630773595

---

### Post by Gallando on 2011-03-24
PNG stores image data in chunks called IDAT in this way:

4 bytes for the length N of the contents
4 bytes saying "IDAT"
N bytes with zlib encoded image data
4 bytes with CRC32b of the preceding N+4 bytes

In your case the first IDAT is N=8192 bytes (very typical) which in hex is: 00 00 20 00 and starts at offset 0x53

So the 2nd IDAT block must start at offset 0x53 + 4 + 4 + 8192 + 4 = 83 + 4 + 4 + 8192 + 4 = 8287 which in hex is 0x205F

But, for some strange reason, your libpng is looking for it at 0x205B (last line of your log), so it looks for the block name ("IDAT") 4 bytes before the right place, finding its length instead (00 00 20 00). Further proof of this is that the previous IDAT block's CRC is taken as the 2nd block's length (last line's -1630773595).

Maybe this strange behavior is due to libpng with 1 bit depth along with your image dimensions (does it happen scanning at other resolutions apart from 300 dpi?)

This is very interesting and unexpected. Can you attach the png file of a blank scan where this happens? also knowing your libpng version would be useful

---

