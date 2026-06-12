---
title: "ATI FGLRX driver + Dell 2405FPW ... wrong resolution (1920x1080)"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by jay.ar.oh on 2007-09-03
Everyone - 

I installed the fglrx driver, both via envy, and after downloading it straight from the ATI website - and no matter what I try, I can't get the desired 1920x1200 resolution - it will only go up to 1920x1080.  This is very strange because I JUST reformatted over a dapper install that worked like a charm at 1920x1200.  

the information on my hardware:  
- of course, the Dell 2405FPW monitor
- the video card...

[B]01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE][/B]

my xorg.conf file:
```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
	Option 		"ConnectedMonitor" "DFP-0"  
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Dell"
	ModelName	"2405FPW"
	DisplaySize     487 304
	
	Modeline "DELL1920"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
	Modeline "DELL1600"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync
	Modeline "DELL1280"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
	Modeline "DELL1152"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
	Modeline "DELL1024"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
	Modeline "DELL800"  48.91  800 840 920 1040  600 601 604 627  -HSync +Vsync
	Modeline "DELL640"  30.72  640 664 728 816  480 481 484 502  -HSync +Vsync

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "ATI"
	Monitor    "Monitor0"
	DefaultColorDepth 24
	SubSection "Display"
		Depth        24
		Modes        "1920x1200"  "1680x1050" "1280x800" "1152x720" "800x500"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection

```

does anyone see any obvious flaws on my part?  What's weird is, I'm looking through the XORG logfile and all mentions of 1920 are coupled with only the 1080 vertical res:

```

(II) fglrx(0): Total of 20 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0): *Mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.0 Hz (I)
(II) fglrx(0): Modeline "1600x1200"  160.96  1600 1704 1880 2160  1200 1201 1204 1242 interlace +hsync
(**) fglrx(0): *Mode "1280x1024": 138.5 MHz (scaled from 0.0 MHz), 80.2 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"  138.54  1280 1368 1504 1728  1024 1025 1028 1069 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"  104.99  1152 1224 1352 1552  864 865 868 902 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 81.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   81.80  1024 1080 1192 1360  768 769 772 802 interlace +hsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 48.9 MHz (scaled from 0.0 MHz), 47.0 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   48.91  800 840 920 1040  600 601 604 627 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 30.7 MHz (scaled from 0.0 MHz), 37.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "640x480"   30.72  640 664 728 816  480 481 484 502 interlace +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(**) fglrx(0): Display dimensions: (487, 304) mm
(WW) fglrx(0): Probed monitor is 520x330 mm, using Displaysize 487x304 mm
(**) fglrx(0): DPI set to (100, 90)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)

```

thanks everyone! I hope someone can help :(

---

### Post by jay.ar.oh on 2007-09-04
*bump* ... anyone? :(

Would switching out the card to NVIDIA make any difference? What's puzzling is that it worked before I formatted.

(and yes, I know I should have backed up my system and/or xorg.conf file ... that one hurts).

---

### Post by kellemes on 2007-09-04
Can you please post the hole /var/log/Xorg.0.log?

---

### Post by jay.ar.oh on 2007-09-04
here's the entire logfile:

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux antec 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep  4 08:10:51 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "ATI"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5b60 card 1002,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5b70 card 1002,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] rev 0, Mem @ 0xd0000000/27, 0xd9000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV370 [Radeon X300SE] rev 0, Mem @ 0xd9010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[1] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[2] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[3] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[6] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[10] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[11] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[12] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[13] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[15] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[16] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[17] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[18] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[1] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[2] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[3] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[6] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[10] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[11] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[12] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[13] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[15] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[16] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[17] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[18] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[6] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[7] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[10] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.40.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.402                    
(II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x5B60) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[6] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[7] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[10] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4648
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[6] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[7] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[10] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X300/X550/X1050 Series" (Chipset = 0x5b60)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0302)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xd9000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RV380
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V380
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: a010  Serial#: 808863571
(II) fglrx(0): Year: 2005  Week: 21
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 52  vert.: 33
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.607
(II) fglrx(0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) fglrx(0): Serial No: T613355H06GS
(II) fglrx(0): Monitor name: DELL 2405FPW
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0010ac10a053473630
(II) fglrx(0): 	150f010380342178eeee50a3544c9b26
(II) fglrx(0): 	0f5054a54b008180a940714fb3000101
(II) fglrx(0): 	010101010101283c80a070b023403020
(II) fglrx(0): 	360007442100001a000000ff00543631
(II) fglrx(0): 	33333535483036475320000000fc0044
(II) fglrx(0): 	454c4c20323430354650570a000000fd
(II) fglrx(0): 	00384c1e5111000a202020202020001e
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/196MHz @ 50Hz [enable load balancing]
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 20 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0): *Mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.0 Hz (I)
(II) fglrx(0): Modeline "1600x1200"  160.96  1600 1704 1880 2160  1200 1201 1204 1242 interlace +hsync
(**) fglrx(0): *Mode "1280x1024": 138.5 MHz (scaled from 0.0 MHz), 80.2 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"  138.54  1280 1368 1504 1728  1024 1025 1028 1069 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"  104.99  1152 1224 1352 1552  864 865 868 902 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 81.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   81.80  1024 1080 1192 1360  768 769 772 802 interlace +hsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 48.9 MHz (scaled from 0.0 MHz), 47.0 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   48.91  800 840 920 1040  600 601 604 627 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 30.7 MHz (scaled from 0.0 MHz), 37.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "640x480"   30.72  640 664 728 816  480 481 484 502 interlace +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(**) fglrx(0): Display dimensions: (520, 330) mm
(**) fglrx(0): DPI set to (93, 83)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
(**) fglrx(0): *Mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync
(**) fglrx(0): *Mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.0 Hz (I)
(II) fglrx(0): Modeline "1600x1200"  160.96  1600 1704 1880 2160  1200 1201 1204 1242 interlace +hsync
(**) fglrx(0): *Mode "1280x1024": 138.5 MHz (scaled from 0.0 MHz), 80.2 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"  138.54  1280 1368 1504 1728  1024 1025 1028 1069 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"  104.99  1152 1224 1352 1552  864 865 868 902 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 81.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   81.80  1024 1080 1192 1360  768 769 772 802 interlace +hsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 48.9 MHz (scaled from 0.0 MHz), 47.0 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   48.91  800 840 920 1040  600 601 604 627 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 30.7 MHz (scaled from 0.0 MHz), 37.6 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "640x480"   30.72  640 664 728 816  480 481 484 502 interlace +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(**) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd9000000 - 0xd900ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[7] -1	0	0xda001000 - 0xda001fff (0x1000) MX[B]
	[8] -1	0	0xda002000 - 0xda002fff (0x1000) MX[B]
	[9] -1	0	0xda003000 - 0xda003fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xda004000 - 0xda004fff (0x1000) MX[B]
	[12] -1	0	0xd9000000 - 0xd900ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xd9010000 - 0xd901ffff (0x10000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[38] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c36000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.40.4
(II) fglrx(0):     Date: Jul 31 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 20.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=4
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x009ea000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,1353)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1080) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 273
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "ConnectedMonitor" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
```

thanks in advance to anyone who might be able to help! :)

---

### Post by jay.ar.oh on 2007-09-06
bump ...

can anyone take a look at this?  I'm completely lost with how to approach this.

---

### Post by zeromerk on 2007-10-25
In Gutsy there's a frontend to the ATI proprietary drivers, where you select GPU/Monitor. Where you select your resolution, make sure the 'widescreen' is checked, it alters your resolution options. 

However, running 1920x1200 doesn't work perfectly for me now. It has the scrolling resolution effect, as if it defaults the monitor for a lower resolution. Haven't figured it out yet, but interested if anybody else is having that problem.

My specs:
OS: Gutsy Gibbon
Monitor: Dell 2405FPW monitor 
GPU: x600
Driver: fglrx

---

### Post by epoch7 on 2008-06-25
i had a very similar problem and posted about it here: [http://ubuntuforums.org/showthread.php?t=751339]("http://ubuntuforums.org/showthread.php?t=751339") let me know if any of this helps...

---

