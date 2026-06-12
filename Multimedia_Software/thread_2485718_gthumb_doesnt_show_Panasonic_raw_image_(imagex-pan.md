---
title: "gthumb doesnt show Panasonic raw image (image/x-panasonic-rw)"
date: 2023-04-07
forum: Multimedia Software
---

### Post by robertonline on 2023-04-07
Hello,
gthumb 3.12.0 does not show Panasonic raw image (image/x-panasonic-rw). Is there any option to make that possible?

Thanks!
Robert

---

### Post by coffeecat on 2023-04-07
My Panasonic Lumix camera produces raw images with the extension .RW2, not .RAW as shown in your image. gThumb version 3.12.0 displays these images just fine for me. Disclaimer - I know little enough about raw images, but I found this: [https://libopenraw.pages.freedesktop.org/formats/rw2/](https://libopenraw.pages.freedesktop.org/formats/rw2/)

From that page:

> Old RAW files don&#8217;t have a preview. Newer one (some RAW and all RW2) have a complete JPEG with Exif embedded.

I wonder if gThumb uses the embedded JPEG for display and your raw files are the older ones. How old is your Panasonic camera?

---

