---
title: "ImageMagick trashes orientation tag on resize"
date: 2009-03-25
forum: Multimedia Software
---

### Post by gysvanzyl on 2009-03-25
I use mogrify from ImageMagick in one of the steps when I create thumbnails from a DVD of archived photos.  Only problem is that it trashes the EXIF orientation tag during resizing, so now all my photos that should display in portrait orientation lie on their sides.

Anyone know of a way around this?  Or even of a better way to create thumbnails.  I basically want to recreate the folder structure of the DVD on a local drive, but instead of the full-sized images (RAW & jpg) I just want 200px thumbnails.

---

### Post by mcduck on 2009-03-25
What exact command are you using? For example "-thumbnail" will strip all EXIF data from images, while doing the same with "-resize" doesn't..

---

### Post by gysvanzyl on 2009-03-25
I have tried with -resize, -scale and -thumbnail, all giving the same result.  I can definitely see that -resize and -scale does not strip the meta data, I still have all the camera info in the resized image.  It's only the orientation tag that's reset to 0.

---

