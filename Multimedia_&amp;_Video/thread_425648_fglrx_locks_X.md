---
title: "fglrx locks X"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Blackiwid on 2007-04-27
I am using at the moment the radeon driver, it works on one dvi output. But the Dual-dvi output is not supported yet. (bug-report is on xorg-bugzilla)

So i want to try the fglrx driver, I tryd it in gentoo with xorg 7.1 and 7.2 -> black screen and x lock, cant switch to console or reboot.

I also tryed the fglrx from feisty, same result. Then i updated to the newest like its described here:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

i used aticonfig to generate xorg.conf and tryed some xorg-config-files from this forum. Same result.

xorg.conf:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
#	Option		"Buttons"		"7"
#	#Option		"Emulate3Buttons"	"true"
#	Option		"ButtonMapping"		"1 2 3 6 7"
#	#Option 		"Resolution"		"100"

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
	Identifier	"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver		"fglrx"
#	BusID		"PCI:5:0:0"
Option "DesktopSetup"  "horizontal,reverse" #Enable Big Desktop
Option "Mode2"         "1280x720" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 31-61
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display. 56-75
EndSection

Section "Monitor"
	Identifier	"P19-1A"
	Option		"DPMS"
#	HorizSync	31-64
#	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Monitor		"P19-1A"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```


xorg-log-file:


```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux black-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 28 00:53:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "P19-1A"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X800 (R430 UO)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
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
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
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
(II) PCI: 00:00:0: chip 10de,02f0 card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 147b,1c26 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 147b,1c26 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 147b,1c26 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 147b,1c26 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 147b,1c26 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 147b,1c26 rev a3 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 147b,1c26 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 147b,1c26 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 147b,1c26 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 147b,1c26 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 147b,1c26 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 147b,1c26 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 147b,1c26 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 02:00:0: chip 1002,554d card 1043,006c rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,556d card 1043,006d rev 00 class 03,80,00 hdr 00
(II) PCI: 03:07:0: chip 104c,8023 card 147b,1c26 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:08:0: chip 10b7,1700 card 10b7,0020 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:16:0), (0,3,3), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) rev 0, Mem @ 0xd0000000/28, 0xfdcf0000/16, I/O @ 0x9c00/8
(--) PCI: (2:0:1) ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary rev 0, Mem @ 0xfdce0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfdef4000 - 0xfdef7fff (0x4000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B](B)
	[10] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[25] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdef4000 - 0xfdef7fff (0x4000) MX[B]
	[1] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[2] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B](B)
	[10] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[15] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[16] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[17] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[18] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[25] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B](B)
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
	[4] -1	0	0xfdef4000 - 0xfdef7fff (0x4000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B](B)
	[14] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B](B)
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
(**) AIGLX disabled
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
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
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.36.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.36g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 17 2007 10:04:46
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.36.1.1.2.3-driver-lnx-x86-x86_64-338188
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x554D) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef4000 - 0xfdef7fff (0x4000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B](B)
	[14] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[31] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[32] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[33] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7c4810
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef4000 - 0xfdef7fff (0x4000) MX[B]
	[5] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[6] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B](B)
	[14] -1	0	0xfdcf0000 - 0xfdcfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[34] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[35] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[36] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DesktopSetup" "horizontal,reverse"
(**) fglrx(0): Option "Mode2" "1280x720"
(**) fglrx(0): Option "HSync2" "65"
(**) fglrx(0): Option "VRefresh2" "60"
(**) fglrx(0): Option "EnablePrivateBackZ" "yes"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI RADEON X800 XL" (Chipset = 0x554d)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x006c)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfdcf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.7
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2003, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: R430
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	ABI class: X.Org Server Extension, version 0.3

```


k i figured it out myself. The problem is that the newer drivers (feisty and gentoo-unstable) dont work at the moment with my card.
I first saw the fglrx working with an old multimedia opengl version of knoppix (xfree 4.3) dri worked.
So i tryed my old debian (was on my server) with fglrx 8.28.2 (etch) and it works also.
Then i tryed the same minimal config (dpkg-reconfigure) in feisty it doesnt work same problems.
Now i am in gentoo and with unstable 8.35.5 fglrx it doenst work with this config neigher.
But then i downgraded to stable 8.32.5 now it works here also.

I will make a new Bugreport on freedesktop.

But i think in feisty that should also not be so?

---

