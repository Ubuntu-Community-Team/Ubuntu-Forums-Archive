---
title: "blank window border when apps maximized"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by adds2one on 2006-11-26
After a long day of work I have Beryl working almost perfectly on my laptop.
The one problem I am having is that if I maximize any apps their window border goes completely white. I can no longer see any of the max/min or close buttons but I can still mouse over where they should be and use them.

Does anyone know how I can fix this. I will give all my info in the hopes that someone will see a solution for me.

I am running Edgy.

Here is the output of glxinfo | grep render

```
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL

```

Here is my relevant xorg.conf settings:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"

Driver "radeon"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
BusID       "PCI:1:0:0"

EndSection

```

---

### Post by monsieurben on 2006-12-02
I had the same problem with my radeon 9200, try replacing "EXA" by "XAA" in "AccelMethod"

here is my "device" section of my xorg.conf (working just great)
```

	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
	Option		"DynamicClocks"		"true"
	Option		"EnablePageFlip"	"true"
	Option		"ColorTiling"		"true"
	Option		"AGPFastWrite"		"true"
	Option		"RenderAccel"		"true"
#	Option		"CRT2Position"		"RightOf"
#	Option		"MergedFB"		"true"


```

Just uncomment the last 2 lines to enable extended desktop, but it doesn't work with beryl.
(sorry for my poor english...)

---

