---
title: "Stutter"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by starorbs on 2006-09-17
I haven't been able to figure out for the life of my why this is happneing. If anyone has any ideas. I installed the repository fglrx ATI drivers, restarted and get about 4700 fps with glxgears, but when I increased the size of the window the gears started stuttering.  This isn't just with the gears any opengl including screensaver stutter. The fps stays the same but whatever is running pretty much pauses briefly every second or so. Anyway some info.
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```
uname
```
Linux laptop 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux

```
lspci
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c5
```
lsmod
```
fglrx                 388908  8
agpgart                34888  2 fglrx,intel_agp

```

Sections in xorg.conf pertaining to video card
```

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection
Section "DRI"
	Mode	0666
EndSection

```

---

