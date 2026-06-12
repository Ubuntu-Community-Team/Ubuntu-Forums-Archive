---
title: "My Right Xinerama Screen Is Dark"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-11-13
I have an IBM/Lenovo ThinkCentre 8808-CW2 with an onboard Intel 810 graphics card, and which I have added an older PCI ATI Mach 64 videocard. I have an IBM ThinkVision LCD Panel  9417-AB1 plugged into each card.

The problem is that with Ubuntu 7.10 (Gutsy), I can't get the Xinerama going. I've tried countless variations from my past successful experiences with Xinerama, but this one eludes me. The symptoms are that I get a perfectly good screen on the left, and on the right I get a black screen and the panel switches off. (I have noticed, however, that if I make both Devices say "Screen 0", the right panel comes on, gives me a mouse but no desktop, and the left panel goes whacky. Therefore, I know I'm getting close.)

If anyone could be so kind as to look at my xorg.conf file and tell me what to try next, I would appreciate it.

```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"device0"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:10:9:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"device0"
	Monitor		"monitor0"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"layout"
	Option		"Clone"	"no"
  screen 0 "screen0" 0 0
  screen 1 "screen1" rightof "screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

```

My Xorg log file is extremely long, so I won't paste it here, but you can ask me questions about it. I did note, however, that it has this failure line in it:

(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x770000)

---

### Post by SuperMike on 2007-11-14
After spending 15 hours on the project, I realized it can't be done. I've decided to bail and move on to a dual head PCI video card.

---

