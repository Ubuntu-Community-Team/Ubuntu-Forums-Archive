---
title: "Shouldn't trident work better than vesa?"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by jordoex on 2007-08-06
I have an old Trident Microsystems TGUI 9440 to use for my second monitor, but oddly, the vesa driver allows a higher resolution than the trident one...  Although it is still not the resolution I want.  trident put it on 640x480 and vesa put it on 800x600, but i want it on 1024x960... Any help, comments or ideas???

BTW, here's my xorg.conf:

```
Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"0 Geforce2"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
#	Screen		0
EndSection

Section "Device"
	Identifier	"1 Trident"
	Driver		"vesa"
	BusID		"PCI:0:9:0"
#	Screen		1
EndSection

Section "Monitor"
	Identifier	"DELL M781s"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"NEC MultiSync 3FGe"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 Geforce2"
	Monitor		"DELL M781s"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "1 Trident"
        Monitor         "NEC MultiSync 3FGe"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	 	"Main Screen"
	Screen          "Second Screen" RightOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option "Xinerama" "true"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection
```

---

