---
title: "Dual Head"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by nextbgates95 on 2008-04-13
ok.  I have a dual head setup with my Radeon X300SE.  MY monitor is connected through the VGA port, and my TV is connected through the s-video port.  I need to have the TV setup to the right of the monitor, but cannot figure it out.

Here is my xorg.conf:
```
# File edited by xorg-edit v07.08.11 at Sun Apr 13 16:27:24 2008

Section "Device"
	Identifier "x300"
	Driver "fglrx"
	BusID "PCI:01:00:0"
EndSection

Section "Monitor"
	Identifier "Dell"
EndSection

Section "Monitor"
	Identifier "TV"
Option		"RightOf" "Dell"

EndSection

Section "Screen"
	Identifier "Screen0"
	Device "x300"
	Monitor "Dell"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Monitor "TV"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	option 		"Xinerama"	"on"
	Screen 		"Screen0"
	Screen		"Screen1" RightOf "Screen0"
EndSection

```

---

