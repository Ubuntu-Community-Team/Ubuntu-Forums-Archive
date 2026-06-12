---
title: "How do I override my monitor refresh rate?"
date: 2009-12-14
forum: Multimedia Software
---

### Post by r2rX on 2009-12-14
Greetz guys,

I'm currently using Ubuntu 9.10 x64, with an ATi 4870. The Catalyst 9.11 drivers are installed and everything is working fine except that I am missing my maximum refresh rates for my monitor. For example, my screen can display 1600x1200 @ 100Hz....but I am restricted to 85Hz.

What is necessary to unlock/enforce the maximum refresh rates of my screen? Or to manually force it?

Also, is it possible to list all the resolutions available for my monitor and assign refresh rates to them that the O/S, no matter what, has to follow?

I'd appreciate all the help. ;)

Here's my xorg.conf, in case you need to know:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
        Option      "HorizSync 30-130"
	Option      "VertRefresh 50-160"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Cheers,

r2rX  :)

---

### Post by r2rX on 2009-12-14
*bump*

Sorry about that.....it's frustrating not knowing what to do. :)

r2rX  :)

---

### Post by r2rX on 2009-12-15
Does no one know a working method of enforcing a range of resolutions, and setting their max refresh rates (that works with the Catalyst 9.11's and Ubuntu 9.10 / RandR)?

r2rX

---

