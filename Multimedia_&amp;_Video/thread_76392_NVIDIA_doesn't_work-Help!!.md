---
title: "NVIDIA doesn't work-Help!!"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by kudu on 2005-10-15
Check this:

glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

What's wrong ?? How do I fix this ?? Need more info just ask.

---

### Post by kudu on 2005-10-15
OK...Panic is over. Got  NVIDIA, but glxgears doesn't work worth the proverbial. How do I fix that ? Runs VERY slow and doesn't read out fps. Should be getting 15000 fps with my GeForce 6800 GT. More or less, that's what I got for a reading in Hoary.

---

### Post by mcduck on 2005-10-15
If you want the fps, you'll have to do 'glxgears -iacknowledgethatthistoolisnotabenchmark'

---

### Post by kudu on 2005-10-16
Got it. Thanks!

---

