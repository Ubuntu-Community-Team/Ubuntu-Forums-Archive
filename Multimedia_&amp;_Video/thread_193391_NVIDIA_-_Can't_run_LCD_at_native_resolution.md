---
title: "NVIDIA - Can't run LCD at native resolution"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by blastus on 2006-06-09
I can't run my LCD at its native 1280x1024 with the NVIDIA driver on Dapper. If I do the picture becomes unstable and every update to the display causes the monitor to black out for several seconds. The picture is also generally unstable, it occasionally shakes a little here and there. 

I need to run at 1280x1024 @ 75 Hz. I've tried everything from "dpkg-reconfigure xserver-xorg" to adding a Modeline to the Monitor section to force the NVIDIA driver to work at 1280x1024 @ 75 Hz but it always shows 1280x1024 @ 60 Hz. The default "nv" driver works and shows 1280x1024 @ 75 Hz.

# V-freq: 75.00 Hz  // h-freq: 80.42 KHz
Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 

My video card is GeForce FX5600 and the manufacturer specs for my LCD are HorizSync 30-81 and VertRefresh 56-75. I am also using a digital DVI cable. I should also point out that this all worked fine on Breezy.

```
dmesg | grep NVIDIA
[4294688.050000] nvidia: module license 'NVIDIA' taints kernel.
[4294688.054000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

Here is a sample of one of the countless xorg.conf settings I've tried:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
EndSection
```

Has anyone had this problem before?

---

### Post by blastus on 2006-06-11
Problem solved!

[NVIDIA: How I fixed my display resolution problem with DVI-D connection!](http://www.ubuntuforums.org/showthread.php?t=194531)

---

