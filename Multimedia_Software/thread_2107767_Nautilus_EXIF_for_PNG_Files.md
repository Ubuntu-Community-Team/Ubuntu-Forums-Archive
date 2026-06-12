---
title: "Nautilus EXIF for PNG Files"
date: 2013-01-22
forum: Multimedia Software
---

### Post by Sam Lars on 2013-01-22
I was using Shotwell to change the EXIF date info for some pictures today and noticed something strange. Nautilus helpfully shows the EXIF data in one tab of the Properties dialog. However, the date info shows up for JPG files and not for PNG files. Gthumb shows the EXIF data is written correctly for both PNG and JPG files.
Is there some reason that Nautilus isn't reading this info from PNG files?

---

### Post by jorok_tupur on 2013-01-26
EXIF for PNG?

[https://en.wikipedia.org/wiki/Exchangeable_image_file_format](https://en.wikipedia.org/wiki/Exchangeable_image_file_format) says that EXIF is not supported in PNG.

---

### Post by AstroLlama on 2013-01-26
> **jorok_tupur said:**
> EXIF for PNG?

[https://en.wikipedia.org/wiki/Exchangeable_image_file_format](https://en.wikipedia.org/wiki/Exchangeable_image_file_format) says that EXIF is not supported in PNG.

[http://stackoverflow.com/questions/9542359/does-png-contain-exif-data-like-jpg](http://stackoverflow.com/questions/9542359/does-png-contain-exif-data-like-jpg)

this post on stack overflow says that though png does NOT support exif it supports "chunks" of meta data. This may account for the way some of the data is preserved. But yes, EXIF data proper is not supported in png.

---

### Post by Sam Lars on 2013-01-26
Thanks for the info about that. I guess the PNG files just have those "chunks" for the metadata.
So does Nautilus only read the EXIF data for the Properties window?

---

