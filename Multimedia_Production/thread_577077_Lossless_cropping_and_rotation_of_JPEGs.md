---
title: "Lossless cropping and rotation of JPEGs"
date: 2007-10-15
forum: Multimedia Production
---

### Post by Endolith on 2007-10-15
I want to do **lossless** cropping and rotation of JPEGs with a graphical editor.  What do people use for this?  gThumb seems to do lossless rotation, but it requires like 6 clicks per image.  Are there any better solutions that also do lossless cropping?

This list might help:

[http://jpegclub.org/losslessapps.html](http://jpegclub.org/losslessapps.html)

---

### Post by rsambuca on 2007-10-15
I have never heard of lossless jpeg cropping.  Is there such a thing?

---

### Post by Endolith on 2007-10-15
> **rsambuca said:**
> I have never heard of lossless jpeg cropping.  Is there such a thing?

Yep.  To an 8 pixel granularity.

JPEGs are just a mosaic of 8x8 pixel discrete cosine transforms.  ;-)  You can throw away some of those 8x8 blocks without losing information from the rest of the image.

---

### Post by Endolith on 2007-10-15
I think this might do it?

[http://pcernoch.wz.cz/PhotoViewer/index.html](http://pcernoch.wz.cz/PhotoViewer/index.html)

But I uh.... can't read that to find out.

---

### Post by rsambuca on 2007-10-16
Try [Google Translate]("http://www.google.com/translate_t").

---

### Post by Endolith on 2007-10-16
> **rsambuca said:**
> Try [Google Translate]("http://www.google.com/translate_t").

Doesn't have that language.

---

### Post by Endolith on 2007-10-16
No ideas?


It seems like command-line jpegtran is my only option, and I'm having trouble thinking of a stupider way to crop images than the command line.  Certainly there are front-ends for it?

---

### Post by kswenson on 2007-11-16
Note that you can chooose a bunch of pictures in gthumb and rotate them all at once.

---

