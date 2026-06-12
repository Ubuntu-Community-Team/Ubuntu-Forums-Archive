---
title: "Dual Monitors - system freezing"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by Thomas_tc on 2006-08-29
Hallo,

I configured xorg.conf for using Dual monitors on my ThinkPad T21. Everything works finde for some time. After different times (1/2h - 3h) the complete Ubuntu 6.0.6 System is freezing. Nothing is reacting and I have to reboot the system. When I use a single-monitor solution with my Laptop - everything works fine, no crash.

Any Ideas how I can specify/solve the problem ?
Thanks,
Thomas

A part of my xorg.conf:

(...)
Section "Device"
	Identifier "S3 Inc. 86C270-294 Savage/IX-MV"
	Driver "savage"
	BusID "PCI:1:0:0"
        Option "BusType" "PCI" 
        Option "DmaMode" "None"
        screen 0
EndSection

Section "Device"
	Identifier "S3 Inc. 86C270-294 Savage/IX-MV 2"
	Driver "savage"
	BusID "PCI:1:0:0"
        Option "BusType" "PCI"
        Option "DmaMode" "None"       
        screen 1
EndSection


Section "Monitor"
	Identifier "ThinkPad T21 TFT"
	HorizSync 28-51
	VertRefresh 43-60
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "NEC MultiSync 5FGe"
	HorizSync 31-62
	VertRefresh 55-90
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "ThinkPad"
	Device "S3 Inc. 86C270-294 Savage/IX-MV"
	Monitor "ThinkPad T21 TFT"
	DefaultDepth 16
	SubSection "Display"
		Depth 1
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "externer Monitor"
	Device "S3 Inc. 86C270-294 Savage/IX-MV 2"
	Monitor "NEC MultiSync 5FGe"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
        Option "Clone" "off"
        Option "Xinerama" "on"
	Screen "ThinkPad"
        Screen "externer Monitor" LeftOf "ThinkPad"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "cursor" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
	InputDevice "Synaptics Touchpad"
EndSection
(...)

---

