---
title: "Xinerama - bad influence on graphics performance"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by lorre on 2006-08-17
Last weekend I did a clean install of Ubuntu because I felt I poluted the OS with everything I tried to get my ATI (X300) in a dual screen setup  working properly. 

After the clean install I installed the latest ATI driver that supports my grahpics card. What I noticed is that after the driver install eveything worked great e.g. google earth worked flawless.

When typing: 'fglrxinfo' I get:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.5946 (8.27.10)
```

The only downside is that I cannot drag windows from 1 screen to another and that if I want a program to be opened in my secondary screen it has to be opened from the panel residing on my secondary screen.

I figured out that adding the following section to my xorg.conf resolved this problem (and I am able to drag windows from 1 screen to another):

```
Section "ServerFlags"
        Option "Xinerama" "true"
EndSection
```

But after doing that I lose my graphics performance (google earth terribly slow). When typing: 'fglrxinfo' after modifying the xorg.conf I now get:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

I assume that's not good. Is there a way to use the xinerama option AND have my graphics card function properly?

---

