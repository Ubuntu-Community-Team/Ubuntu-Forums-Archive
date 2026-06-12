---
title: "915M can´t change refresh rate..."
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by Basotang on 2007-02-27
Dear all,

On a DELL D610 laptop, I am running Edgy, I did intall 915resolution and configure (sudo dpkg-reconfigure xserver-xorg)
However, I do not manage to change the refresh rate of the motinor I use. I found the proper settings for the monitor (iiyami vision master pro 410), but I can't manage to change the resolution!

Any idea what I am doing wrong?
Thanks a lot in advance,

Seb.

Please find below relevant parts of my xorg.conf and log attached:

====
Section "Device"
	Identifier	"Mobile Intel 915GM"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection


Section "Monitor"
    Identifier    "Pro Master 410"
    Option        "DPMS"
    HorizSync    27-96
    VertRefresh    50-160
    Option          "UseEdidFreqs"          "false"
    Option          "UseEDID"               "false"
    Option          "ModeValidation"        "NoEdidModes"
    
    # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
    Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

    # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
    Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
    
    # 1400x1050 @ 75.00 Hz (GTF) hsync: 82.20 kHz; pclk: 155.85 MHz
    Modeline "1400x1050_75.00"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"CRT Screen"
	Device		"Mobile Intel 915GM"
	Monitor		"Pro Master 410"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Mobile Intel 915GM"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"CRT Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
====
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): config file hsync range 27-96kHz not within DDC hsync ranges.
(WW) I810(0): config file vrefresh range 50-160Hz not within DDC vrefresh ranges.
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 9152 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1121 pages failed
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(WW) I810(0): Bogus panel fit register, Xvideo positioning may not be accurate.
(WW) I810(0): Using fallback ratio - was 0x230bc, now 0x10681
(WW) I810(0): Option "UseFBDev" is not used
(WW) I810(0): Option "UseEdidFreqs" is not used
(WW) I810(0): Option "UseEDID" is not used
(WW) I810(0): Option "ModeValidation" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) I810(0): Changing XVideo pipe (1 to 0).
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 10176 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1121 pages failed
(WW) I810(0): Extended BIOS function 0x5f64 failed.
(WW) I810(0): Extended BIOS function 0x5f64 failed.
(WW) I810(0): Failed to set display devices to 0x900.
(WW) I810(0): Enabling LVDS directly. Pipe B.
(WW) I810(0): Enabling ADPA directly. Pipe B.
(WW) I810(0): Writing config directly to SWF0.
(WW) I810(0): Changing XVideo pipe (0 to 1).
(WW) I810(0): Changing XVideo pipe (1 to 0).
===

---

