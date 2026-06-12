---
title: "TV-OUT ATI Cards/Somewhat generic question"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by dwessell on 2006-03-02
Hi all..

I have installed the ATI drivers for a Radeon 9600 card..

But... How does one activate the TV-Out for an S-video card? Is it a combo of keystrokes?



Thanks
David

---

### Post by dwessell on 2006-03-02
Whew..

:)

I've learned a lot.. I've got the TV displaying, but I can't figure out how to make the monitor display on it's own resolution.. RIght now it's way to huge (And in black and white) on the TV..

I would eventually like the monitor and the TV to be independed of each other, but for now, I'm just working on making the TV work..

Any suggestions on how to change the monitor resolution?

Thanks
David


```

Section "Monitor"
	Identifier   "KDS K700"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "ati"
	BusID       "PCI:3:0:0"
	Option	    "TVOutFormat" "SVIDEO"
	Option	    "TVStandard" "NTSC-M"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "TVOutFormat" "SVIDEO"
	Option	    "TVStandard" "NTSC-M"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor    "KDS K700"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by toorima on 2006-03-02
I think you forgot to put modes in your screen for the tv, if you change your config like this it should work
```

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes		"800x600"
	EndSubSection
EndSection

```

Here is my config and it works exept I get black and white too but that could be my tv
```

Section "Device"
	Identifier	"ATI0"
	Screen		0
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section	"Device"
	Identifier	"ATI1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"COMPOSITE"
	Option		"TVStandard"	"PAL-B"
	Option		"ConnectedMonitor"	"TV"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"HorizSync"	"30-50"
	Option		"VertRefresh"	"50"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section	"Screen"
	Identifier	"Screen1"
	Device		"ATI1"
	Monitor		"TV"
	DefaultDepth	24
	SubSection	"Dsiplay"
	Depth		24
	Modes		"640x480"
#	Modes		"800x600"
EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 	"Screen0"
	Screen 1 	"Screen1" rightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by dwessell on 2006-03-03
toorima,


I did add that, but it just kicks both into 800x600 mode, instead of letting me specify different resolutions for each (TV&Monitor).

I've been pouring through the X site, and the ATI site, looking for a guide on the .conf file..

I'm sure that there has to be a seperate option for each screen, but I've not been able to analyze it yet..

Any other pointers would be welcome.

Thanks
David

---

### Post by dwessell on 2006-03-04
I'm still running into a brick wall with this.. When I start X with my current config file, I lose the monitor, and the display goes out to the TV.. But not sized to the TV correctly, and in black and white..

I'm running an Svideo cord to the Svideo connector on a DVD player, then that goes into the TV via a coax...

I know I can get color, as on the same computer under Windows, it just works :)

Here's my updated xorg.conf, any thoughts appreciated..

dw
```

Section "Monitor"
	Identifier   "KDS K700"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option	    "TVOutFormat" "SVIDEO"
	Option	    "TVFormat" "NTSC-M"
	Option	    "DesktopSetup" "clone"
	Option	    "OverlayOnCRTC2" "0"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor    "KDS K700"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection




```

---

### Post by dwessell on 2006-03-07
For future searchers, reverting back to drivers 8.20 worked..

dw

---

