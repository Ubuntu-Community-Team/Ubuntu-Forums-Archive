---
title: "&quot;No libGL on this box&quot;"
date: 2008-04-23
forum: Multimedia Software
---

### Post by djbon2112 on 2008-04-23
I can't find a straight answer anywhere. They all simply say "use the hardware accelerated driver" or something equally stupid. Well, I am using the latest nVidia driver from their site, installed and activated using the Restricted Driver Manager, and I still get this stuff (err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !) when I try to run OpenGL programs.

Here's glxinfo |grep -i -e direct -e vendor:

```
joshua@joshua-laptop:~$ glxinfo |grep -i -e direct -e vendor
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Any help appreciated!

---

### Post by djbon2112 on 2008-04-24
Anyone? I just want to play Peggle!

---

### Post by xc3RnbFO8P on 2008-04-24
Look at this:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/192490](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/192490)

---

### Post by djbon2112 on 2008-04-24
Followed [http://ubuntuforums.org/showthread.php?t=698805](http://ubuntuforums.org/showthread.php?t=698805) to the letter, and it still doesn't work. Yes, I've rebooted.

```
joshua@joshua-laptop:~$ glxinfo
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
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by djbon2112 on 2008-05-19
I've tried following multiple fixes for this bug, but none of them seem to work. Does anyone have any additional suggestions?

---

