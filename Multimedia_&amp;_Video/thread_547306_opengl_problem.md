---
title: "opengl problem"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by inflamous on 2007-09-09
I followed this guide, [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide), to get the ati driver (I have an ATI Radeon Xpress 1150), and then the troubleshooting guide ([http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)), but I still have no 3D acceleration, whenever I do **fglrxinfo**, I get:

[I]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/I]

instead of something like this:

[I]display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)[/I]


In the last line of the troubleshooting, it tells me to open and comment out any line with fglrx in /etc/modprobe.d/blacklist-restricted, but that file doesn't even exist on my computer.

I'm using Feisty Kubuntu and playing Supertuxkart or any opengl game is impossible because of this problem.

Any help?

---

### Post by inflamous on 2007-09-09
Wow, stupid me, I suddenly realize I followed the wrong guide...

---

