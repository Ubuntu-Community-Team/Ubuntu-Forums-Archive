---
title: "How do i get my second graphics card working?"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by SJobberling on 2008-03-07
I have two 3850hds in my main box at the moment in windows i run them in crossfire for gaming and tri or quad head for work. I was hoping that in linux i would be able to do the same (i know crossfire doesnt work in linux) and run more than 2 moniters. But after several attempts with multiple distros the best i can do is the standard dual head setup. I have attempted to use the xinerama tutorials all over the net and in this forum but have been stumped by the way that xorg is managed by aticonfig. can anyone explain to me how to get my second card to work?


Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0   "aticonfig-Screen[0]"
    Screen       1   "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    Option "Xinerama" "true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
        BusID           "PCI:1:0:0"
	Screen          0
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	BusID           "PCI:2:0:0"
	Screen          1
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes   "1920x1200"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes   "1440x900"
	EndSubSection
EndSection


Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

