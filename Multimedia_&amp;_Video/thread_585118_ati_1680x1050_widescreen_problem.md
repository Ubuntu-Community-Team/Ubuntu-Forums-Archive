---
title: "ati 1680x1050 widescreen problem"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by jzippo on 2007-10-21
Some basic specs first:
Fujitsu Siemens Scenic D, i845, PM
256 Mb PC133
20Gb Barracuda HD
Radeon RV100 [Radeon 7000/VE]
Monitor is a 22" widescreen from LG, model L226WTQ-WF (bought in Sweden).

In Ubuntu 7.04 I couldn't get the image centred on my screen in 1680x1050 - even after adjusting the image on my screen using the monitor's controls to its maximum horizontal position the monitor still showed a black band about 1 cm wide on the left side of the screen. To remedy this I would fire up xvidtune from the terminal and adjust the position of the image. 

Now, after upgrading to 7.10 the image is too wide. If we adopt the menu row at the top of the screen as the point of reference the screen shows the desktop beginning with "System" and ends at the last number of the current time (at Sun Oct 21, 5:30, where only about half of the zero is showing). My monitor does not provide any controls for adjusting the width of the image. So I tried to use xvidtune again but, alas, it no longer allows me to change any of the timing options. When I try to make the image narrower and click on "Test" it only gives me a message stating "Invalid Mode requested" and "Sorry: You have requested a mode-line That is not possible, or not supported by your hardware configuration". Interestingly, I also get this message if I try to adjust the image in exactly in the same way as I was able to do in Ubuntu 7.04 (that is, moving the image to the left). As a linux noob (my sixth day using linux) my understanding now is that there's some kind of problem related to the video mode that could perhaps be remedied by specifying a modeline in xorg.conf. I tried to generate one using 'gtf 1680 1050 60' and got back: Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync. I removed '_60" in the resolution name and pasted the Modeline into xorg.conf. It now looks like this (with irrelevant sections culled):
```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"L226WTQ"
	Option		"DPMS"
	HorizSync	28-83
	VertRefresh	56-75
	Modeline 	"1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -Hsync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"L226WTQ"
	DefaultDepth	24
	SubSection "Display"
		Depth	24		
		Modes	"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I reboot the machine and the image is still too wide. I type "xvidtune -show" to find out what the current modeline is and get back: "1680x1050"   119.00   1680 1728 1760 1840   1050 1053 1059 1080 -hsync +vsync" which is not at all what I specified in xorg.conf (I have double and triple checked the modeline in xorg.conf). So, once again, I am the end of my rope. Hopefully someone else knows how to force the Modeline to be used or what else I could do. 

Here's my /var/log/xorg.0.log:
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux omega 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 21 17:56:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "L226WTQ"
(**) |   |-->Device "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 110a,0087 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 12 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 12 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 110a,0055 rev 12 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 110a,0055 rev 12 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 110a,0055 rev 12 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 110a,0055 rev 12 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 110a,0056 rev 12 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5159 card 174b,7112 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 1106,3044 card 1106,3044 rev 46 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 8086,3014 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 1814,0301 card 1458,e934 rev 00 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe8100000 - 0xe81fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xe8000000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xec000000 from 0xefffffff to 0xebffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[1] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[2] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[3] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[4] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[7] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[8] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[9] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[10] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[11] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[12] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[13] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[1] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[2] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[3] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[4] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[7] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[8] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[9] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[10] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[11] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[12] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[13] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	[4] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[5] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[6] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[7] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[8] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[13] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[14] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[17] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon VE/7000 QY (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[5] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[6] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[7] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[8] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[13] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[14] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[17] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[5] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[6] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[7] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[8] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[16] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[17] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[18] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xe8000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon VE/7000 QY (AGP/PCI)" (ChipID = 0x5159)
(--) RADEON(0): Linear framebuffer at 0xf0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit SDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=60 min=12000 max=35000; xclk=15500
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Output VGA-0 using monitor section L226WTQ
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 22093
(II) RADEON(0): Not using mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 +hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output VGA-0 using initial mode 1680x1050
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (490, 320) mm
(**) RADEON(0): DPI set to (87, 95)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xe800ffff (0x10000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe8100000 - 0xe8107fff (0x8000) MX[B]
	[7] -1	0	0xe8108000 - 0xe8108fff (0x1000) MX[B]
	[8] -1	0	0xe8109000 - 0xe81097ff (0x800) MX[B]
	[9] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[10] -1	0	0xe8000000 - 0xe800ffff (0x10000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[15] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[19] -1	0	0x00004000 - 0x0000407f (0x80) IX[B]
	[20] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[23] -1	0	0x00001400 - 0x0000140f (0x10) IX[B]
	[24] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[25] -1	0	0x00002400 - 0x0000240f (0x10) IX[B]
	[26] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xf0000000,0x2000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1728,4854)
(II) RADEON(0): Reserved area from (0,1200) to (1728,1202)
(II) RADEON(0): Largest offscreen area available: 1728 x 3652
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1023000
(II) RADEON(0): Will use depth buffer at offset 0x180c000
(II) RADEON(0): Will use 0 kb for textures at offset 0x1ff5000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0b7a000
(II) RADEON(0): [drm] mapped SAREA 0xe0b7a000 to 0xb7b9c000
(II) RADEON(0): [drm] framebuffer handle = 0xf0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x1a30; Card 0x1002/0x5159]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xec000000
(II) RADEON(0): [agp] Ring mapped at 0xb7a9b000
(II) RADEON(0): [agp] ring read ptr handle = 0xec101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7a9a000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xec102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb57c6000
(II) RADEON(0): [agp] GART texture map handle = 0xec302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb52e6000
(II) RADEON(0): [drm] register handle = 0xe8000000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 21
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xf3fff000 is: 0xf3fff000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xec7fec00
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xec7fec00
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		31 256x256 slots
		13 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1728 x 3649
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 474 x 296
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 22093
(II) RADEON(0): Not using mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 +hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: GSM  Model: 564d  Serial#: 207557
(II) RADEON(0): Year: 2007  Week: 3
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 49  vert.: 32
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 28  H max: 83 kHz, PixClock max 150 MHz
(II) RADEON(0): Monitor name: L226WTQ
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d4d56c52a0300
(II) RADEON(0): 	031101036a312078eaaec5a2574a9c25
(II) RADEON(0): 	125054a76b80950f950081808140714f
(II) RADEON(0): 	0101010101017c2e90a0601a1e403020
(II) RADEON(0): 	3600da281100001a21399030621a2740
(II) RADEON(0): 	68b03600da281100001c000000fd0038
(II) RADEON(0): 	4b1c530f000a202020202020000000fc
(II) RADEON(0): 	004c3232365754510a20202020200002
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) RADEON(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync
(II) RADEON(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) RADEON(0): EDID vendor "GSM", prod id 22093
(II) RADEON(0): Not using mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync (64.7 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 +hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)

```

This is my monitors .inf file as provided by LG
```

;===============================================================

; [L226WTQ.inf]

; Revision 1.3   January-08-2007

; Copyright(c)1998~2007 LG Electronics Inc.,All Rights Reserved.

;===============================================================

;

[Version]

signature="$CHICAGO$"

Class=Monitor

ClassGuid={4D36E96E-E325-11CE-BFC1-08002BE10318}

Provider=%LG%

CatalogFile=L226WTQ.cat

DriverVer=01/08/2007,1.3



[ControlFlags]

ExcludeFromSelect.NT=Monitor\GSM564D

ExcludeFromSelect.NT=Monitor\GSM564E



[DestinationDirs]

DefaultDestDir = 11

L226WTQ_Analog.CopyFiles = 23

L226WTQ_Digital.CopyFiles = 23



[SourceDisksNames]

1=%DiskName%,,,



[SourceDisksFiles]

L226WTQ.ICM=1



[Manufacturer]

%LG%=LG,NTamd64



[LG]

%L226WTQ_Analog%=L226WTQ_Analog.Install,Monitor\GSM564D

%L226WTQ_Digital%=L226WTQ_Digital.Install,Monitor\GSM564E



[LG.NTamd64]

%L226WTQ_Analog%=L226WTQ_Analog.Install,Monitor\GSM564D

%L226WTQ_Digital%=L226WTQ_Digital.Install,Monitor\GSM564E



[L226WTQ_Analog.Install]

DelReg=DEL_CURRENT_REG

AddReg=L226WTQ_Analog.AddReg,1680,DPMS

CopyFiles=L226WTQ_Analog.CopyFiles



[L226WTQ_Digital.Install]

DelReg=DEL_CURRENT_REG

AddReg=L226WTQ_Digital.AddReg,1680,DPMS

CopyFiles=L226WTQ_Digital.CopyFiles



[DEL_CURRENT_REG]

HKR,MODES

HKR,,MaxResolution

HKR,,DPMS

HKR,,ICMProfile



[1680]

HKR,,MaxResolution,,"1680,1050"



[DPMS]

HKR,,DPMS,,1



[L226WTQ_Analog.AddReg]

HKR,"MODES\1680,1050",Mode1,,"28.0-83.0,56.0-75.0,+,+"

HKR,,PreferredMode,,"1680,1050,59"

HKR,,ICMprofile,0,"L226WTQ.ICM"



[L226WTQ_Digital.AddReg]

HKR,"MODES\1680,1050",Mode1,,"28.0-83.0,56.0-75.0,+,+"

HKR,,PreferredMode,,"1680,1050,59"

HKR,,ICMprofile,0,"L226WTQ.ICM"



[L226WTQ_Analog.CopyFiles]

L226WTQ.ICM



[L226WTQ_Digital.CopyFiles]

L226WTQ.ICM



[Strings]

DiskName="LG Monitor Profiles Installation Disk"

LG="LG"

L226WTQ_Analog="LG L226WTQ(Analog)"

L226WTQ_Digital="LG L226WTQ(Digital)"


```

---

### Post by jzippo on 2007-10-21
Adding Option "DDC" "false" to the "Monitor" section made X obey the modeline at least. But now there's a black band on the left side of the screen.

---

### Post by jzippo on 2007-10-21
Ok, after four days of tweaking and reading I was finally able to solve this. First problem was that I thought my screen had a 60Hz refresh when in fact it is at 59Hz. I realized this by running 'sudo ddcprobe' in a terminal where I got this listing:

```

vbe: VESA 2.0 detected.
oem: ATI RADEON VE
memory: 32768kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)

edid: 
edid: 1 3
id: 564d
eisa: GSM564d
serial: 00032ac5
manufacture: 3 2007
input: separate sync, sync on green, analog signal.
screensize: 49 32
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 1440x1440@75
ctiming: 1440x1440@60
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1152x864@75
dtiming: 1680x1050@59
dtiming: 1680x1050@77
monitorrange: 28-83, 56-75
monitorname: L226WTQ

```

Actually, it showed that there were two modes for 1680x1050 and none of them were at 60Hz. I decided to use the 1680x1050@59 as my starting point because my monitor's inf-file listed this as the preferred mode (HKR,,PreferredMode,,"1680,1050,59", the last number being the refresh rate). I generated a modeline using the preferred resolution and the new refresh rate: "gtf 1680 1050 59". The result I got was 

```

# 1680x1050 @ 59.00 Hz (GTF) hsync: 64.07 kHz; pclk: 144.55 MHz
  Modeline "1680x1050_59.00"  144.55  1680 1784 1968 2256  1050 1051 1054 1086  -HSync +Vsync

```

I pasted the modeline into xorg.conf and rebooted X (Ctrl+Alt+Backspace) after which I selected the 1680x1050@59 resolution using System->Preferences->Screen Resolution. (One important step before rebooting is to put in Option "DDC" "false" into the monitor section so that the modeline is obeyed no matter what). This made the image on the screen jump to the right leaving a black band on the left. I was unable to adjust this using the monitor's controls.  Therefore, I tweaked the 4th and 5th value appearing after Modeline a couple of times until I got a satisfactory result. The image was not quite centered but hitting the auto/set button made the image perfectly centered and flicker free. This is the xorg.conf that finally solved my problems:

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"L226WTQ"
	Option		"DPMS"
	Option		"DDC"	"false"
	HorizSync	28-83
	VertRefresh	56-75
	Modeline	"1680x1050@59" 144.55 1680 1946 2130 2256 1050 1051 1054 1086
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"L226WTQ"
	DefaultDepth	24
	SubSection "Display"
		Depth	24		
		Modes	"1680x1050@59" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

This fixed the resolution on my desktop but, in doing so, it also made my login screen look weird (flickering and off center). This problem I can probably fix with another modeline for the login screen resolution (I believe I could glean this bit of info from /var/log/xorg.0.log).

---

### Post by SouthernPott on 2007-11-06
Hi, I am having a similar problem with different hardware.  Viewsonic VG2230wm 22" widescreen monitor with Powercolor ATI Radeon 9200 256mb video card.

I am new to Ubuntu so most of your analysis was above me although I could follow it a little.  Presently I am dual booting XP Home and Ubuntu 7.10 so that I can adjust slowly.

In XP Home when I boot up the screen resolution fills the monitor perfectly and the settings are on 1680x1050 at 60Hz.  In Ubuntu it shows the same settings but the screen resolution is shifted to the right approximately 1/2 cm.  This causes the up and down scroll bar to be hidden as well as most of the log off/shutdown icon in the upper right corner and the 1/2cm black band on the left side of the screen.

I can adjust it manually on the monitor but then when I boot into XP the screen resolution is shifted 1/2cm to the left leaving the black band on the right side of the screen.

Consequently, to use both operating systems I am having to make manual adjustments to center the screen.

If I adjust the monitor, through the terminal, will I maintain my settings in XP?  Are you running a single OS or dual booting?

My other problem really doesn't apply to this specific topic and is happening in both XP and Ubuntu.   My video card has VGA and DVI ports,  The monitor also has these ports.  I can use the VGA port without a problem and it shows ANALOG when the monitor comes on.  I want to switch it to DIGITAL and it should work although I have been unsuccessful to this point.  This is also a manual setting on the monitor. 

When I have only the VGA cable attached it works fine but is ANALOG.

When I have both the VGA and the DVI cables attached it shows as dual monitors in the graphics setup on XP.  I can change some of the settings in the graphics setup and either it still sets up as ANALOG or I get a very fuzzy screen if I switch it to DIGITAL.

When I have only the DVI cable attached it boots up to the blue on light, then shuts down to the amber sleep light. 

I know this isn't enough information to go on yet but if the setting should be 59Hz rather than 60Hz, is this something that will throw off these types of functions?

Thanks for any thoughts and help.

Malcolm

---

### Post by SouthernPott on 2007-11-06
This is what I get with xvidtune -show.

"1680x1050"   146.25   1680 1784 1960 2240   1050 1053 1059 1089 +hsync -vsync

Besides being new to Ubuntu I am also learning to use the terminal so I don't really know what to do with it yet.

Malcolm

---

### Post by SouthernPott on 2007-11-06
vbe: VESA 2.0 detected.
oem: ATI RADEON 9200
memory: 262144kb
mode: 800x600x16
mode: 1024x768x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x25 (text)
mode: 132x43 (text)
edid: 
edid: 1 3
id: a21e
eisa: VSCa21e
serial: dadb6101
manufacture: 52 2006
input: separate sync, composite sync, sync on green, analog signal.
screensize: 47 30
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1680x1680@60
ctiming: 1600x1200@60
ctiming: 1440x1440@60
ctiming: 1400x1050@60
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1152x864@75
dtiming: 1680x1050@77
monitorserial: QC9065200341
monitorrange: 30-82, 50-75
monitorname: VG2230wm
malcolm@Dell-Dimension:~$

---

### Post by SouthernPott on 2007-11-06
I haven't solved my problems yet but I can live with them.  My monitor has settings for "auto select" which I haven't used before.  I had been adjusting the horizontal positioning before which is way too slow a process.  It would still be better to have it set on boot up but I can live with this until I am more familiar with changing things.

I looked at the xorg.0.log.0 but it is 3800+ lines long.  Is this the normal look or can I reset it and get a smaller view? 

Still appreciate any thoughts or help.

Malcolm

---

### Post by n6rob on 2007-11-30
Malcolm,

I have the same monitor that you do.  I too am having some pretty serious problems getting set the way I want it.  Thanks for posting the information about ddcprobe and xvidtune -show; that helps.  I am still testing my system.  I have an Nvidia card; not ATI. But I have a very similar resolution issue.  I can't decide if the monitor has faulty EDID or if the Nvidia card can't handle the resolution.  I am running DVI mode on Gutsy.  I cannot get 1680x1050; the only res it gives me is 1600x1200.

My ddcprobe comes back as

vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - q162-4nz Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

Notice how it says the EDID fails.  If I learn anything new I'll post back here.

Rob

---

### Post by SouthernPott on 2007-11-30
Hi Rob,

Are you only running with the DVI cable.  My issues actually started with WinXP.  I think when I first got this monitor, back in March or April, I hooked up the DVI cable to the DVI connector on the video card and it actually worked but I don't remember what the screen resolution settings were.  I know I changed it to 1650x1080 and it stopped working.  When I use the VGA connections and cable it works but only for analog.  Not bad but I know the digital look is much smoother.

Right now I only have the VGA cable hooked up.  I may have to change the resolution settings in XP to a lower level and see if I can use the DVI cable again.  Then go from there.  Hopefully if I can get it to work on the XP side, I can dig into Ubuntu more and find a better setting.

I called both the video card manufacturer and Viewsonic for help several months ago but didn't get anywhere.  Finding this topic is the first glimmer of hope I have had.

My real problem is that while I can follow the directions of the first poster, I don't know what to do with the information yet.  He got two refresh rates for 1650x1080 while I only get 77 Hz.  

Wish I could help you with the edidfail.  I did a Google search because I didn't know what edid was and got this link for a bug report.

[https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994]("https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/94994")

Might be something in there that makes sense to you.

---

