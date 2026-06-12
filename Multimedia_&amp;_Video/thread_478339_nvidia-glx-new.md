---
title: "nvidia-glx-new"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by ehmdjii on 2007-06-19
hello, i tried to install the nvidia drivers for my graphics card (GeForce 8600 GT) by

apt-get install nvidia-glx-new

but unfortunately now no opengl works at all. this is the output from glxinfo

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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by cogadh on 2007-06-19
Check the sticky at the top of the forum for nVidia install instructions. There are additional steps you need to take after running the install package.

---

### Post by dabl on 2007-06-19
Your 8600 card is pretty new.  Here is information about setting it up with the new driver:

[http://ubuntuforums.org/showthread.php?t=453942&highlight=8600+gt&page=2](http://ubuntuforums.org/showthread.php?t=453942&highlight=8600+gt&page=2)
:)

---

