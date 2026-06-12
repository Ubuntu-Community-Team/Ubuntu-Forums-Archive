---
title: "Xorg.0.log error and nVidia TV out settings"
date: 2008-12-08
forum: Multimedia Software
---

### Post by slaabrockband on 2008-12-08
Os: ubuntu 8.10
graphics  Geforce 7500 Le
driver NVIDIA  177.82
TV and AV cables, ports checked. They work fine.
computer HP pavilion model a1628sc

I have used this guide for setting up xorg.config for seperate x screens:
[http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)


I have tried to set up a additional Tv- screen via S-video. I get absolutely nothing on the TV Screen.


Here is a part of my Xorg.0.log file - Please help me make a understandable interpretation of this message :

> (--) NVIDIA(1): Connected display device(s) on GeForce 7500 LE at PCI:1:0:0:
(--) NVIDIA(1):     Sony CPD-2001GT (CRT-1)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): Sony CPD-2001GT (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(EE) NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) NVIDIA(1):     MetaMode "1024x768" is not supported on this GPU; none is
(EE) NVIDIA(1):     recommended, instead.
(WW) NVIDIA(1): No valid modes for "832x624"; removing.
(EE) NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) NVIDIA(1):     MetaMode "800x600" is not supported on this GPU; none is
(EE) NVIDIA(1):     recommended, instead.
(WW) NVIDIA(1): No valid modes for "720x400"; removing.
(EE) NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) NVIDIA(1):     MetaMode "640x480" is not supported on this GPU; none is
(EE) NVIDIA(1):     recommended, instead.





Here is a part of my xorg.config    despite eventual faults  - I should at least expect some kind of a reaction on the tv-screen ? 
Am I right or wrong ?


> Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 7500 LE"
	BusID		"PCI:1:0:0"
	Option  "RenderAccel"   "true"
	screen 0
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Device"
	Identifier      "Device1"
	Screen 1
	Option          "TVOutFormat" "SVIDEO" #or SVIDEO Composite etc
	Option          "TVStandard" "PAL-B" #or NTSC etc
	Option          "ConnectedMonitor" "TV"
	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Modes	 "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Device "Device1"
	Identifier "Screen1"
	Monitor "TV"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


---

### Post by slaabrockband on 2008-12-09
bump

---

