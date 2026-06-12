---
title: "9800pro  driver problems"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by stratotak on 2006-10-26
Ok..Fresh install of latest Ubuntu.Installed fglrx drivers and modules .Rebooted ,but when I run fglrxinfo i get..
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
...
this is the driver section from my  xorg.conf..
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

When i do lsmod  it shows fglrx module loaded and  modprobe fglrx has no errors.The fglrx module loads and everything seems to be fine.Its just seems to not be using it.With the xorg ati driver I had max resolution of 1024x768,but after I installed fglrx driver I now have 1280x1024 resolution.
When I run glgears i get  error..
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).

Anyway..anyone know what problem is and how to get it working ??thanks

---

