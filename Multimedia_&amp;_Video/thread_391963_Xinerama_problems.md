---
title: "Xinerama problems"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by nicholas on 2007-03-23
Hi, I followed the instructions [here]("http://www.ubuntuforums.org/showthread.php?p=1773624") to enable dual graphics card and monitor support under Feisty but it doesn't work.

After a restart of X with Ctrl-Alt-BkSpc, the main display on the NVidia card works as per normal, but the monitor connected to the Voodoo PCI card stays switched off.

Any help would be greatly appreciated.

Here is my xorg.conf

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
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Screen		0
	Option		"AddARGBVisuals"		"True"
	Option		"AddARGBGLXVisuals"		"True"
#	Option		"NoLogo"			"True"
	Option 		"DDCMode" 			"True"
EndSection

Section "Device"
	Identifier	"Voodoo Card"
	Driver		"tdfx"
	BusID		"PCI:4:6.0"
	Screen		1
#	Option		"AddARGBVisuals"		"True"
#	Option		"AddARGBGLXVisuals"		"True"
#	Option		"NoLogo"			"True"
	Option 		"DDCMode" 			"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Voodoo Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Voodoo Screen"
	Device		"Voodoo Card"
	Monitor		"Voodoo Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen"
	Screen  1   	"Voodoo Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option 		"Xinerama" 	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by djf_jeff on 2007-03-23
Can you post the content of the file /var/log/Xorg.0.log please? It can give people more informations to find the problem you have.

---

### Post by nicholas on 2007-03-24
> **djf_jeff said:**
> Can you post the content of the file /var/log/Xorg.0.log please? It can give people more informations to find the problem you have.

thanks for trying to help, hope this makes it a little easier for you.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux aisha 2.6.20-12-lowlatency #2 SMP PREEMPT Wed Mar 21 20:58:11 UTC 2007 i686
Build Date: 20 March 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 24 02:33:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Screen "Voodoo Screen" (1)
(**) |   |-->Monitor "Voodoo Monitor"
(**) |   |-->Device "Voodoo Card"
(EE) Screen Main Screen doesn't exist: deleting placement
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
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) PCI: 00:00:0: chip 10de,02f1 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81bf rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0242 card 1043,81bf rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81c0 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1043,81c0 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81c0 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81c0 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81c0 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81c0 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81c0 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,81c0 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:06:0: chip 121a,0005 card 121a,0057 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf6a00000 - 0xfaafffff (0x4100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xbbf00000 - 0xbfefffff (0x4000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51G [GeForce 6100] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
(--) PCI: (4:6:0) 3Dfx Interactive, Inc. Voodoo 3 rev 1, Mem @ 0xf8000000/25, 0xbc000000/25, I/O @ 0xc800/8, BIOS @ 0xfaaf0000/16
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
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(WW) TDFX: No matching Device section for instance (BusID PCI:4:6:0) found
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.08
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(II) UnloadModule: "tdfx"
(II) Unloading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[10] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[11] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[17] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(WW) NVIDIA(0): Option "DDCMode" is not used
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by nicholas on 2007-03-24
Ok, I've found two typo's in xorg.conf and changed them.

They were:

> 	BusID		"PCI:4:6.0"

changed to:

> 	BusID		"PCI:4:6:0"

and

> 	Screen  1   	"Voodoo Screen" LeftOf "Main Screen"

changed to:

> 	Screen  1   	"Voodoo Screen" LeftOf "Default Screen"

Still no joy.

These two errors in Xorg.0.log worry me:

> (WW) TDFX: No matching Device section for instance (BusID PCI:4:6:0) found
(--) Chipset 3dfx Voodoo3 found
> (EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "tdfx"

The first is bizarre as earlier on in the log it clearly finds the card, and PCI address matches the xorg.conf:

> (--) PCI: (4:6:0) 3Dfx Interactive, Inc. Voodoo 3 rev 1, Mem @ 0xf8000000/25, 0xbc000000/25, I/O @ 0xc800/8, BIOS @ 0xfaaf0000/16

The second is mad because my xorg.con has:

> Section "Screen"
	Identifier	"Voodoo Screen"
	Device		"Voodoo Card"
	Monitor		"Voodoo Monitor"
        etc.............


Full Xorg.0.log follows:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux aisha 2.6.20-12-lowlatency #2 SMP PREEMPT Wed Mar 21 20:58:11 UTC 2007 i686
Build Date: 20 March 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 24 05:07:15 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Screen "Voodoo Screen" (1)
(**) |   |-->Monitor "Voodoo Monitor"
(**) |   |-->Device "Voodoo Card"
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
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) PCI: 00:00:0: chip 10de,02f1 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81bf rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0242 card 1043,81bf rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81c0 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1043,81c0 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81c0 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81c0 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81c0 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81c0 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81c0 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,81c0 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:06:0: chip 121a,0005 card 121a,0057 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf6a00000 - 0xfaafffff (0x4100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xbbf00000 - 0xbfefffff (0x4000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51G [GeForce 6100] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
(--) PCI: (4:6:0) 3Dfx Interactive, Inc. Voodoo 3 rev 1, Mem @ 0xf8000000/25, 0xbc000000/25, I/O @ 0xc800/8, BIOS @ 0xfaaf0000/16
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
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(WW) TDFX: No matching Device section for instance (BusID PCI:4:6:0) found
(--) Chipset 3dfx Voodoo3 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "tdfx"
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[36] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.08
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     OEC (CRT-0)
(--) NVIDIA(0): OEC (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[10] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[11] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[17] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[35] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[39] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(WW) NVIDIA(0): Option "DDCMode" is not used
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by nicholas on 2007-03-24
I'm going greyer by the minute. :-(

If I try the Voodoo card on it's own with this xorg.conf it works fine.

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Voodoo Card"
	Driver		"tdfx"
	BusID		"PCI:4:6:0"
EndSection

Section "Monitor"
	Identifier	"Voodoo Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Voodoo Screen"
	Device		"Voodoo Card"
	Monitor		"Voodoo Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen     	"Voodoo Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"BackingStore"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If I try the following xorg.conf which *should* enable the NVidia and the Voodoo cards only the NVidia springs into life.

> Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

# NVidia Card, Monitor and Screen settings
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Screen		0
	Option		"AddARGBVisuals"		"True"
	Option		"AddARGBGLXVisuals"		"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
# End of NVidia Card, Monitor and Screen settings

# Voodoo Card, Monitor and Screen settings
Section "Device"
	Identifier	"Voodoo Card"
	Driver		"tdfx"
	BusID		"PCI:4:6:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Voodoo Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Voodoo Screen"
	Device		"Voodoo Card"
	Monitor		"Voodoo Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
# End of Voodoo Card, Monitor and Screen settings

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen"
	Screen  1   	"Voodoo Screen" LeftOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"Xinerama" 	"true"
	Option 		"BackingStore"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

The resulting Xorg.0.log is as follows:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux aisha 2.6.20-12-lowlatency #2 SMP PREEMPT Wed Mar 21 20:58:11 UTC 2007 i686
Build Date: 20 March 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 24 07:14:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Screen "Voodoo Screen" (1)
(**) |   |-->Monitor "Voodoo Monitor"
(**) |   |-->Device "Voodoo Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f1 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81bf rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81bf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0242 card 1043,81bf rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81c0 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1043,81c0 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81c0 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81c0 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81c0 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81c0 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81c0 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,81c0 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:06:0: chip 121a,0005 card 121a,0057 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf6a00000 - 0xfaafffff (0x4100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xbbf00000 - 0xbfefffff (0x4000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51G [GeForce 6100] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
(--) PCI: (4:6:0) 3Dfx Interactive, Inc. Voodoo 3 rev 1, Mem @ 0xf8000000/25, 0xbc000000/25, I/O @ 0xc800/8, BIOS @ 0xfaaf0000/16
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
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[3] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[4] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[5] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[11] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[17] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[1] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[2] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[3] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(WW) TDFX: No matching Device section for instance (BusID PCI:4:6:0) found
(--) Chipset 3dfx Voodoo3 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "tdfx"
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[7] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[8] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[9] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[14] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[36] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.08
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     OEC (CRT-0)
(--) NVIDIA(0): OEC (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[10] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[11] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xbbf00000 - 0xbbf0ffff (0x10000) MX[B](B)
	[17] -1	0	0xbc000000 - 0xbdffffff (0x2000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[35] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[39] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

Please someone help me!  Anyone? :-o

---

### Post by nicholas on 2007-03-24
Ok, after much pissing about I have managed to get it working.

It was the Screen 0/Screen 1 lines in the Device sections that caused the trouble.

Final working xorg.conf is:

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
	Load  "record"
	Load  "GLcore"
	Load  "glx"
	Load  "extmod"
	Load  "dri"
	Load  "xtrap"
	Load  "dbe"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

# NVidia Card, Monitor and Screen settings
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option         "RenderAccel" "true"
	Option         "BackingStore" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
# End of NVidia Card, Monitor and Screen settings

# Voodoo Card, Monitor and Screen settings
Section "Device"
	Identifier	"Voodoo Card"
	Driver		"tdfx"
	VendorName  	"3Dfx Interactive, Inc."
	BoardName   	"Voodoo 3"
	BusID       	"PCI:4:6:0"
	Option      	"BackingStore" "true"
EndSection

Section "Monitor"
	Identifier	"Voodoo Monitor"
	HorizSync    	31.0 - 54.0
	VertRefresh  	50.0 - 120.0
	Option		"DPMS"
	Modeline 	"1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Voodoo Screen"
	Device		"Voodoo Card"
	Monitor		"Voodoo Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes "1024x768"
	EndSubSection
EndSection
# End of Voodoo Card, Monitor and Screen settings

Section "ServerFlags"
    Option		"Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 	0	"Default Screen"
	Screen	1	"Voodoo Screen" LeftOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by nicholas on 2007-03-25
I'd just like to add....

Thanks for the deluge of help folks, it's true what they say... The Ubuntu community are the most helpful people in the whole of Linuxdom!

---

