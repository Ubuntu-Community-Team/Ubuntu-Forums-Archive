---
title: "multidisplay questions"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by Craig Watson on 2006-07-02
Hi everyone
I've had a few problems lately and wanted to know a few things..

I have an AGP Radeon 9200 (dualhead) and a PCI Radeon 9250 (dualhead also) I just bought. My screens are: 1 HP P1120 (primary, center, 21"), 1 HP P1110 (secondary, left, 21"), both connected to the Rad 9200,  and one Compaq MV740 (tertiary, right, 17"), connected to the 9250. I currently have a resolution of 1600x1200 on each of the big screens.

So anyway, here goes:

1: If possible, how can I have a triple display setup, with Xinerama (or MergedFB, or Ati Big desktop) ? The small screen can only go up to 1280x1024, will I need a bigger screen ?(I can get an equivalent of the 2 others without too much difficulty)

2: How can I have 3D acceleration on several screens? I had it working with MergedFB as well as with the ATi big desktop (long ago, the only time the driver would work ^^) but that stopped at more or less a quarter of the second display (2048 limit). I saw something about it on the dri wiki, that apparently it could be solved, but found nothing on HOW to solve it. Is it possible?

3: This setup works in windows (3200x1200 plus 1280x1024, all in big desktop with the ati drivers, with direct rendering on the first two (connected to AGP card) and indirect on the third one. Does this mean there's hope with the linux drivers? (They're a real pain in the a**, I'll need a clean install just to install the drivers, let alone make them work)

Here's my Xorg.conf, if that's any help. I've got Xinerama with a 3200x1200 resolution on the Agp card , but it just won't use the pci one (plus, the livecd won't start X if the pci card is connected)
Some of it was generated automatically (screen modes for the first 2, input devices, modules and files) and I edited the rest.

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
	Identifier	"Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Radeon 9200"
	VendorName	"ATi"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Radeon 9200 2"
	VendorName	"ATi"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"Radeon 9250"
	VendorName	"ATi"
	Driver		"radeon"
	BusID		"PCI:0:11:0"
	Screen		2
EndSection

#Section "Device"
#	Identifier	"Radeon 9250 2"
#	VendorName	"ATi"
#	Driver		"radeon"
#	BusID		"PCI:0:11:0"
#	Screen		3
#EndSection

Section "Monitor"
	Identifier	"HP P1120"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"HP P1110"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Compaq MV740"
	Option		"DPMS"
	HorizSync	31-70	
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"P1120"
	Device		"Radeon 9200 2"
	Monitor		"HP P1120"
	DefaultDepth	24
	SubSection "Display"
#		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"P1110"
	Device		"Radeon 9200"
	Monitor		"HP P1110"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"MV740"
	Device		"Radeon 9250"
	Monitor		"Compaq MV740"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
	Option		"Xinerama" "on"
EndSection

Section "ServerLayout"
	Identifier	"Triple Head Layout"
	Screen		0 "P1120" 0 0
	Screen		1 "P1110" RightOf "P1120"
	Screen		2 "MV740" LeftOf "P1120"
	InputDevice	"Keyboard"
	InputDevice	"Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

Thanks for reading all this crap ;) and thanks for any help

EDIT: Forgot to add that when I boot the computer with this setup, X tries to start, 3rd monitor switched on, but then X hangs and everything stays blank. I have to comment out the lines referring to the pci card, or disconnect it, for it to work.. any ideas why this happens? Also, mergedFB worked (with acceleration, but then X wouldn't start when I rebooted the computer...

---

### Post by Craig Watson on 2006-07-03
I've tried changing the display settings in the "system settings" (kde), but apparently that only wants two monitors. when I try changing the status of the third monitor (second card) from "unused" to "secondary", it disactivates the current secondary screen. Would that have anything to do with X hanging when the third screen is "activated" in xorg.conf?
any reply would be appreciated ^^

---

