---
title: "Unable to Configure RV100 Grahic Card"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by NuttBoxer on 2007-11-25
I have a RV100 ATI graphic card that I have been unable to configure on the latest version of Ubuntu(7.10).  From all the forum and howto's I've read, it seems that this card should configure automatically via the default drivers.  Maybe this is why there are no howto's for older graphics cards.  This is my VGA info:

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
02:0b.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

I think the problem is related to this error message I keep receiving when I try to view anything having to do with my glx:

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
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

I am fairly new at using Linux, so I'm hoping this is something very simple I'm just not aware of.  Any help is appreciated.

---

