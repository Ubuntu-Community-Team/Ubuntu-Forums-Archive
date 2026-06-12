---
title: "Need Help Radeon 9600 driverr"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by encikraju on 2008-04-17
theres a lot of problem regarding my video card and the display.
i've been trying hundreds of how to and not much helps.
anyway my problem is my display are very laggy right now i.e. when opening opera + scrolling down page
i'm using gutsy

here's some info
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

Segmentation fault (core dumped)

```



```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

sudo gedit /etc/X11/xorg.conf
!!nothing

glxgears
-crashed and another login appear

Any ideas?
or how to restart it all over again /default?

---

