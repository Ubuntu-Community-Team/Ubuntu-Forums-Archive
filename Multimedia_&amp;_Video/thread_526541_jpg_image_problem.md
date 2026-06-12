---
title: "jpg image problem"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Astrikor on 2007-08-15
I am having a problem opening jpg files.
I get a message "Image has zero width" and the screen just shows a question mark.
I have tried Gimp, gthumb and image viewer - no success.

Any ideas?

---

### Post by dougfractal on 2007-08-15
> **Astrikor said:**
> I am having a problem opening jpg files.
I get a message "Image has zero width" and the screen just shows a question mark.
I have tried Gimp, gthumb and image viewer - no success.

Any ideas?
is it all jpegs?
cloud be a library problem, reinstall jpeg  library?

ls -lh *.jpg

---

### Post by Astrikor on 2007-08-15
[QUOTE=dougfractal;3195551]is it all jpegs?]


NO, it looks like any jpgs over 1mb.  Smaller ones are ok

---

### Post by dougfractal on 2007-08-15
can you test with imagemagick

sudo apt-get install imagemagick
> display myjpeg.jpg

---

