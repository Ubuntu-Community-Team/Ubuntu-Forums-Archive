---
title: "switching between multiple server layouts"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by cius on 2006-12-22
I have a dual head setup in xorg on Ubuntu Edgy using the nvidia driver.  Here is my xorg.conf:

```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"6800XT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen   	0
#	Option          "RenderAccel"       "true"
EndSection

Section "Device"
	Identifier	"6800XT-TV"
	Driver    	"nvidia"
	Screen          1
	BusID           "PCI:1:0:0"
	Option   	"TVOutFormat" "S-VIDEO"
	Option    	"TVStandard"  "NTSC-M"
	Option          "ConnectedMonitor" "TV"
EndSection

Section "Monitor"
	Identifier	"DELL D1226H"
	Option		"DPMS"
	Modeline "1600x1200_70.00"  190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync
	Modeline "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
	Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync
	Modeline "800x600_70.00"  45.50  800 840 920 1040  600 601 604 625  -HSync +Vsync
	Modeline "640x480_70.00"  28.56  640 664 728 816  480 481 484 500  -HSync +Vsync
	HorizSync	30-95
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier 	"TV"
	HorizSync	30-150
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"6800XT"
	Monitor		"DELL D1226H"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200_70.00" "1280x1024_70.00" "1024x768_70.00" "800x600_70.00" "640x480_70.00"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TVScreen"
	Device   	"6800XT-TV"
	Monitor  	"TV"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"800x600_60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerLayout"
	Identifier	"Dual"
	Screen  0 	"Default Screen"
	Screen  1 	"TVScreen" LeftOf "Default Screen"
EndSection

Section "ServerLayout"
	Identifier	"TVOnly"
	Screen   	"TVScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option          "Composite"         "Enable"
EndSection

```

The Default server layout works fine, as does the Dual server layout when I invoke startx with "-- -layout Dual".  However, when I invoke: > startx -- -layout TVOnly  Xorg does not start properly.  It dies with an error saying: > (WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) Screen 0 deleted because of no matching config section.
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining. Would anyone happen to see what I'm doing wrong?  I would like to have a server layout so that I can startx only on my TV after changing to a virtual terminal and stopping gdm.  I do this with the Dual server layout to watch movies, but I prefer to play games on my television and using the Dual server layout tends to slow down the game.  I assume this is because the other screen active in the Dual configuration takes up valuable resources.  Any help wth this issue will be greatly appreciated.

---

