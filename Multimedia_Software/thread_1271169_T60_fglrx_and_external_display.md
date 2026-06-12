---
title: "T60 fglrx and external display"
date: 2009-09-20
forum: Multimedia Software
---

### Post by Harpalus on 2009-09-20
I've recently purchased a fancy new monitor, specifically a P2370, and I've been given nothing but headaches over it. I plugged it in, and it worked..alright, I suppose. The natural resolution of the display is 1920x1080, and it was only displaying a clone of my current desktop, at 1680x1050, which made the picture all fuzzy and warped. After some googling and fiddling and mucking about, I finally got everything working great. Laptop resolution at the native 1680x1050, external at 1920x1080, can move windows back and forth in between them....

Except movies wouldn't play. It took me a bit to figure out that fglrx had been disabled. I enabled it again, and everything went pear-shaped. It's been an absolute nightmare. Wading through aticonfig, xrandr, xinerama, everything I could think of....I simply can't do it. All I want to do is set up my external monitor as a second desktop at 1920x1080, in tandem with my 1680x1050 LCD, but all it can do is display them both at 1680x1050 (or lower), which warps the image and gives me a headache to even look at.

No matter how hard I try I can't get the resolution of the external monitor to 1920x1080. My graphics card is an ATI Radeon x1400, and I'm using 8.10.

This is my current xorg.conf file, without the comments at the beginning. I have indeed tried to fiddle with the various aticonfig options. It's possible I missed something, but...this is just one of at least 30 different xorg.conf's I've tried, all to no avail. Can anybody please help?

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "mirror"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

