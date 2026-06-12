---
title: "Intel Graphics Problem"
date: 2009-01-01
forum: Multimedia Software
---

### Post by NickRich on 2009-01-01
Using 8.10 with no luck running 3d apps,  Compiz works fine but everything else fails.  The card is an integrated intel chipset.  Ive searched everywhere for a solution, tried every driver / fix that I've been able to locate.  Any help would be greatly appreciated.

glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

xdriinfo driver 0
i965


Im pretty sure the problem is due to the OpenGL rendering being set to software even though is my integrated video is capable of hardware rendering.

---

### Post by NickRich on 2009-01-02
bump...
anyone?  any suggestions?

---

### Post by thread on 2009-01-19
This sounds darn similar to my issue... More info in this thread:

[http://ubuntuforums.org/showthread.php?t=1033566](http://ubuntuforums.org/showthread.php?t=1033566)

---

