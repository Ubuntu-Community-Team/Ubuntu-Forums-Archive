---
title: "wanting a split screen w/ 2 monitors"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by philipscard on 2005-11-18
Seems getting dual monitors working is a very common request, but I can't find anything on the web describing a generic way to proceed, or even how to get things like xinerama or the ATI Big Desktop...

What I have: Apple Powerbook G3 (Lombard), running Kubuntu Breezy/Mac OS8, with an Apple Multiscan 15" AV CRT monitor attached (presumably another firm's reboxed screen, but I can't find out which, definitely not Sony). At present, without any intervention from me, both show the same desktop. Boot and startup texts appear on the external monitor. Both run at 1024x768, but the only refresh rates in the 'system setting' app are 29, 30 and 32Hz - painful on the CRT (bizarrely, changing it introduces lots of errors into graphics on the LCD...).

What I would very much like: one big desktop spread across both screens, both at 1024x768, but with the CRT @ 75Hz, and with the LCD as the main (startup) monitor.

Some relevant extracts from my xorg.conf:

Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage LT Pro"
	Driver		"ati"
	BusID		"PCI:0:17:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage LT Pro"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection



Any advice appreciated (all installation instructions as apt-get please - having updated to breezy the new package manager is tragically slow (unusably so)).
Thanks.

---

### Post by Teroedni on 2005-11-18
[http://www.linux-magazine.com/issue/17/DualHead.pdf](http://www.linux-magazine.com/issue/17/DualHead.pdf)

very good howto for this ;)

You can check it there and do it yourself , or i can do it for you if you want:)

---

