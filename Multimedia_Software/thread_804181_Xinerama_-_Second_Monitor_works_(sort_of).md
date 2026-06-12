---
title: "Xinerama - Second Monitor works (sort of)"
date: 2008-05-22
forum: Multimedia Software
---

### Post by hbarnwheeler on 2008-05-22
I've been fooling around trying to get xinerama working.  It now does, but only sort of.  My secondary screen works, but only sort of.  I can move windows there, but, well, there is some kind of rendering problem.  When I move a window, it either disappears or renders incorrectly.  Screenshot below:

[IMG]http://i25.tinypic.com/xmk9qq.jpg[/IMG]

xorg.conf: 
```
# xorg.conf (X.Org X Window System server configuration file)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

  Screen      0  "screen1" 0 0
  #Screen      1  "screen2" RightOf "screen1"
  Screen      1  "screen2" Relative "screen1" 1280 256
	
Option "Xinerama" "true"

EndSection


Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	#Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"

	SubSection "Display"
		Depth	24
	Modes "1280x1024"
	EndSubSection
EndSection

Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 765MB/715MB/CD175D(P)"
	Horizsync	30-85
	Vertrefresh	50-160
	Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 

	Gamma	1.0
EndSection

Section "device" #  
	Identifier	"device2"
	Boardname	"Voodoo Banshee (generic)"
	Busid		"PCI:4:5:0"
	Driver		"tdfx"
        Option	"dpms"	"on"
        Option	"dri"	"false"
        Option	"NoAccel" "false"
	#Screen	1
EndSection

Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	
  SubSection "Display"
	Depth	24
	Modes "1024x768"
  EndSubSection

EndSection

Section "Monitor"

    Identifier  "monitor2"
    
# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   31-70

#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 55-120
    #Modeline "1024x768" 85 1024 1032 1152 1360 768 784 787 823
    Modeline "1024x768" 81.55  1024 1064 1168 1352   768  768  770  804 


EndSection
Section "ServerFlags"
EndSection
```

X log:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux uncle-bilbo 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 22 18:49:30 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "screen1" (0)
(**) |   |-->Monitor "monitor1"
(**) |   |-->Device "device1"
(**) |-->Screen "screen2" (1)
(**) |   |-->Monitor "monitor2"
(**) |   |-->Device "device2"
(**) Option "Xinerama" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f1 card 1019,1b32 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1019,1b32 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1019,1b32 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 0000,0000 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1019,1b32 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0242 card 10de,0242 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 10de,cb84 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1019,1b32 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1019,1b32 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 1019,1b32 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1019,1b32 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1019,1b32 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card f019,1b32 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1019,1b32 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:2: chip 10de,026b card 1019,1877 rev a2 class 04,01,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1019,1b32 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:05:0: chip 121a,0003 card 1092,8030 rev 03 class 03,00,00 hdr 00
(II) PCI: 04:06:0: chip 1102,0004 card 1102,0052 rev 03 class 04,01,00 hdr 80
(II) PCI: 04:06:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 04:07:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51G [GeForce 6100] rev 162, Mem @ 0xfb000000/24, 0xd0000000/28, 0xfc000000/24
(--) PCI: (4:5:0) 3Dfx Interactive, Inc. Voodoo Banshee rev 3, Mem @ 0xec000000/25, 0xf8000000/25, I/O @ 0xcc00/8
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
	[0] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[1] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[2] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[1] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[2] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
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
	[4] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[29] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[29] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
(--) Chipset 3dfx Banshee found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[29] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[35] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[36] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[37] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[40] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.02
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) TDFX(1): Softbooting the board (through the int10 interface).
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:04:05.0/rom: got 32KB
(II) TDFX(1): Softbooting the board succeeded.
(II) TDFX(1): TDFXFindChips: found 1 chip(s)
(**) TDFX(1): Depth 24, (--) framebuffer bpp 32
(==) TDFX(1): RGB weight 888
(==) TDFX(1): Default visual is TrueColor
(**) TDFX(1): Option "NoAccel" "false"
(**) TDFX(1): Option "DRI" "false"
(--) TDFX(1): Chipset: "3dfx Banshee"
(--) TDFX(1): Linear framebuffer at 0xF8000000
(--) TDFX(1): MMIO registers at addr 0xEC000000
(--) TDFX(1): PIO registers at addr 0xCC00
(II) TDFX(1): DRAMINIT1 read 0x40284030, programming 0x40202031 (not Banshee)
(II) TDFX(1): TDFXInitChips: numchips = 1
(II) TDFX(1): TDFXInitChips: cfgbits = 0x00000000, initbits = 0x00000001
(II) TDFX(1): TDFXInitChips: mem0base = 0xec000000, mem1base = 0xf8000008
(II) TDFX(1): TDFXInitChips: mem0size = 0x02000000, mem1size = 0x02000000
(II) TDFX(1): TDFXInitChips: mem0bits = 0x00000005, mem1bits = 0x00000050
(II) TDFX(1): TDFXInitChips: cfgbits = 0x00000055
(II) TDFX(1): TDFXInitChips: MMIOAddr[0] = 0xec000000
(II) TDFX(1): TDFXInitChips: LinearAddr[0] = 0xf8000008
(--) TDFX(1): VideoRAM: 16384 kByte Mapping 32768 kByte
(==) TDFX(1): Using gamma correction (1.0, 1.0, 1.0)
(II) TDFX(1): monitor2: Using hsync range of 31.00-70.00 kHz
(II) TDFX(1): monitor2: Using vrefresh range of 55.00-120.00 Hz
(II) TDFX(1): Clock range:  12.00 to 270.00 MHz
(II) TDFX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "1280x960" (hsync out of range)
(II) TDFX(1): Not using default mode "640x480" (hsync out of range)
(II) TDFX(1): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(1): Not using default mode "640x512" (hsync out of range)
(II) TDFX(1): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(1): Not using default mode "640x512" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(1): Not using default mode "896x672" (hsync out of range)
(II) TDFX(1): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(1): Not using default mode "896x672" (hsync out of range)
(II) TDFX(1): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(1): Not using default mode "928x696" (hsync out of range)
(II) TDFX(1): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "928x696" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(1): Not using default mode "576x432" (hsync out of range)
(II) TDFX(1): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 151000 greater than 135000
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 155800 greater than 135000
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 184000 greater than 135000
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "960x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "960x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "2048x1536" (hsync out of range)
(II) TDFX(1): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) TDFX(1): Virtual size is 1024x768 (pitch 1024)
(**) TDFX(1): *Mode "1024x768": 81.5 MHz, 60.3 kHz, 75.0 Hz
(II) TDFX(1): Modeline "1024x768"x75.0   81.55  1024 1064 1168 1352  768 768 770 804 (60.3 kHz)
(==) TDFX(1): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) TDFX(1): ShowCache Disabled
(**) TDFX(1): video key default 0x1e
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TDFX(1): initializing int10
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:04:05.0/rom: got 32KB
(II) TDFX(1): VESA BIOS detected
(II) TDFX(1): VESA VBE Version 3.0
(II) TDFX(1): VESA VBE Total Mem: 16384 kB
(II) TDFX(1): VESA VBE OEM: 3Dfx Interactive, Inc.
(II) TDFX(1): VESA VBE OEM Software Rev: 1.0
(II) TDFX(1): VESA VBE OEM Vendor: Elpin Systems, Inc.
(II) TDFX(1): VESA VBE OEM Product: 3Dfx Banshee
(II) TDFX(1): VESA VBE OEM Product Rev: Version 1.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) TDFX(1): VESA VBE DDC supported
(II) TDFX(1): VESA VBE DDC Level 2
(II) TDFX(1): VESA VBE DDC transfer in appr. 8 sec.
(II) TDFX(1): VESA VBE DDC read successfully
(II) TDFX(1): Manufacturer: NEC  Model: 5dc4  Serial#: 16843009
(II) TDFX(1): Year: 2000  Week: 20
(II) TDFX(1): EDID Version: 1.2
(II) TDFX(1): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) TDFX(1): Sync:  Separate  Composite
(II) TDFX(1): Max H-Image Size [cm]: horiz.: 33  vert.: 24
(II) TDFX(1): Gamma: 2.20
(II) TDFX(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) TDFX(1): First detailed timing is preferred mode
(II) TDFX(1): redX: 0.629 redY: 0.334   greenX: 0.289 greenY: 0.599
(II) TDFX(1): blueX: 0.148 blueY: 0.067   whiteX: 0.283 whiteY: 0.297
(II) TDFX(1): Supported VESA Video Modes:
(II) TDFX(1): 720x400@70Hz
(II) TDFX(1): 720x400@88Hz
(II) TDFX(1): 640x480@60Hz
(II) TDFX(1): 640x480@67Hz
(II) TDFX(1): 640x480@72Hz
(II) TDFX(1): 640x480@75Hz
(II) TDFX(1): 800x600@56Hz
(II) TDFX(1): 800x600@60Hz
(II) TDFX(1): 800x600@72Hz
(II) TDFX(1): 800x600@75Hz
(II) TDFX(1): 832x624@75Hz
(II) TDFX(1): 1024x768@60Hz
(II) TDFX(1): 1024x768@70Hz
(II) TDFX(1): 1024x768@75Hz
(II) TDFX(1): Manufacturer's mask: 0
(II) TDFX(1): Supported Future Video Modes:
(II) TDFX(1): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) TDFX(1): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) TDFX(1): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) TDFX(1): #3: hsize: 1152  vsize 864  refresh: 70  vid: 19057
(II) TDFX(1): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) TDFX(1): Supported additional Video Mode:
(II) TDFX(1): clock: 94.5 MHz   Image Size:  310 x 232 mm
(II) TDFX(1): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) TDFX(1): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) TDFX(1): Ranges: V min: 55  V max: 120 Hz, H min: 31  H max: 70 kHz, PixClock max 110 MHz
(II) TDFX(1): Monitor name: AccuSync 70
(II) TDFX(1): Serial No: 0503027YA
(II) TDFX(1): EDID (in hex):
(II) TDFX(1): 	00ffffffffffff0038a3c45d01010101
(II) TDFX(1): 	140a01020c211878ea2118a1554a9926
(II) TDFX(1): 	11484cffee00315945596159714a8140
(II) TDFX(1): 	010101010101ea240060410028303060
(II) TDFX(1): 	130036e81000001e000000fd0037781f
(II) TDFX(1): 	460b000a202020202020000000fc0041
(II) TDFX(1): 	63637553796e632037300a20000000ff
(II) TDFX(1): 	003035303330323759410a202020000a
(II) TDFX(1): EDID vendor "NEC", prod id 24004
(II) TDFX(1): Using hsync ranges from config file
(II) TDFX(1): Using vrefresh ranges from config file
(II) TDFX(1): Printing DDC gathered Modelines:
(II) TDFX(1): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) TDFX(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) TDFX(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) TDFX(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) TDFX(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) TDFX(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) TDFX(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) TDFX(1): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) TDFX(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) TDFX(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) TDFX(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) TDFX(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) TDFX(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) TDFX(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) TDFX(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) TDFX(1): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) TDFX(1): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) TDFX(1): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) TDFX(1): Modeline "1152x864"x69.8   96.75  1152 1224 1344 1536  864 867 871 902 -hsync +vsync (63.0 kHz)
(II) TDFX(1): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[1] 1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xeffff000 - 0xeffff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[38] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[39] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[40] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[43] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprD)
	[44] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprD)
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(==) TDFX(1): Write-combining range (0xf8000000,0x2000000)
(II) TDFX(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0xc900
(II) TDFX(1): Changing back offset from 0x009ff000 to 0x009fe000
(II) TDFX(1): Textures Memory 5.42 MB
(II) TDFX(1): Cursor Offset: [0x00000000,0x00001000)
(II) TDFX(1): Fifo Offset: [0x00001000, 0x00041000)
(II) TDFX(1): Front Buffer Offset: [0x00041000, 0x00493000)
(II) TDFX(1): Texture Offset: [0x00493000, 0x009FE000)
(II) TDFX(1): BackOffset: [0x009FE000, 0x00CFE000)
(II) TDFX(1): DepthOffset: [0x00CFF000, 0x00FFF000)
(II) TDFX(1): Minimum 338, Maximum 1279 lines of offscreen memory available
(II) TDFX(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Driver provided NonTEGlyphRenderer replacement
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(==) TDFX(1): Backing store disabled
(==) TDFX(1): Silken mouse enabled
(**) Option "dpms" "on"
(**) TDFX(1): DPMS enabled
(WW) TDFX(1): Direct rendering disabled
(==) RandR enabled
(II) Setting vga for screen 0.
Screen 0 is using RAC for mem
Screen 1 is using RAC for mem
(II) Screen 0 shares mem resources
(II) Screen 1 shares mem resources
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
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) NVIDIA: Xinerama and GLX are enabled, but some X screens are not being
(WW) NVIDIA:     driven by the NVIDIA X driver.  OpenGL rendering will be
(WW) NVIDIA:     disabled on these screens:
(WW) NVIDIA:  - Screen 1: TDFX

```

---

