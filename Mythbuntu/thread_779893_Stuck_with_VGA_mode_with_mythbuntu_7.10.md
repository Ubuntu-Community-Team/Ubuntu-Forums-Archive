---
title: "Stuck with VGA mode with mythbuntu 7.10"
date: 2008-05-03
forum: Mythbuntu
---

### Post by coscos on 2008-05-03
Hi guys, I got a problem with my mythbuntu box (7.10) -- It always starts with vga mode. If I remove its fail safe xorg file in /etc/X11 dir, the system will keep trying to detect the right resolution but never come back with the right one. My LCD is capable of 1920x1080p.

Please help!

My Machine:

MB: Gigabyte GA-G33M-S2H, 
CPU: Intel E2160
Video Card: Onboard GA3100
LCD: Olevia 247TFHD 1080p
2GB RAM

Xorg.0.log:

> 

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux mocha 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http:/ / wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/ var/ log/ Xorg.0.log", Time: Sat May  3 00:08:10 2008
(EE) Unable to locate/ open config file
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading / usr/ lib/ xorg/ modules/ / libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,29c2 card 1458,d000 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,29c3 card 1458,d000 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a022 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2918 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2921 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 02:00:0: chip 197b,2368 card 1458,b000 rev 00 class 01,01,85 hdr 00
(II) PCI: 03:05:0: chip 10ec,8167 card 1458,e000 rev 10 class 02,00,00 hdr 00
(II) PCI: 03:07:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/ O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/ O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:4), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/ O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf0ffffff (0x1000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/ O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf1000000 - 0xf2ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0xf3100000/ 19, 0xe0000000/ 28, 0xf3000000/ 20, I/ O @ 0xe200/ 3
(--) PCI: (0:2:1) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0xf3180000/ 19
New driver is "i810"
(==) Using default built-in configuration (55 lines)
(==) --- Start of built-in configuration ---
	Section "Module"
		Load	"extmod"
		Load	"dbe"
		Load	"glx"
		Load	"freetype"
		Load	"type1"
		Load	"record"
		Load	"dri"
	EndSection
	Section "Monitor"
		Identifier	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vga Device 0"
		Driver	"vga"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vga Screen 0"
		Device	"Builtin Default vga Device 0"
		Monitor	"Builtin Default Monitor"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default vga Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default i810 Screen 0" (0)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default i810 Device 0"
(**) |-->Screen "Builtin Default fbdev Screen 0" (1)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default vesa Device 0"
(**) |-->Screen "Builtin Default vga Screen 0" (3)
(**) |   |-->Monitor "Builtin Default Monitor"
(**) |   |-->Device "Builtin Default vga Device 0"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "<default keyboard>"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
(WW) The core keyboard device wasn't specified explicitly in the layout.
	Using the default keyboard configuration.
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/ usr/ share/ fonts/ X11/ cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/ var/ lib/ defoma/ x-ttcidfont-conf.d/ dirs/ TrueType" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/ usr/ share/ fonts/ X11/ misc,
	/ usr/ share/ fonts/ X11/ 100dpi/ :unscaled,
	/ usr/ share/ fonts/ X11/ 75dpi/ :unscaled,
	/ usr/ share/ fonts/ X11/ Type1,
	/ usr/ share/ fonts/ X11/ 100dpi,
	/ usr/ share/ fonts/ X11/ 75dpi
(==) RgbPath set to "/ etc/ X11/ rgb"
(==) ModulePath set to "/ usr/ lib/ xorg/ modules"
(II) Open ACPI successful (/ var/ run/ acpid.socket)
...
(II) LoadModule: "extmod"
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / libextmod.so
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
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading / usr/ lib/ xorg/ modules/ / fonts/ libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "record"
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "i810"
(II) Loading / usr/ lib/ xorg/ modules/ drivers/ / i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "fbdev"
(II) Loading / usr/ lib/ xorg/ modules/ drivers/ / fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.3.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vesa"
(II) Loading / usr/ lib/ xorg/ modules/ drivers/ / vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vga"
(II) Loading / usr/ lib/ xorg/ modules/ drivers/ / vga_drv.so
(II) Module vga: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "mouse"
(II) Loading / usr/ lib/ xorg/ modules/ input/ / mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading / usr/ lib/ xorg/ modules/ input/ / kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/ 855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(II) VGA: Generic VGA driver (version 4.1) for chipsets: generic
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading / usr/ lib/ xorg/ modules/ linux/ / libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.2
(EE) open / dev/ fb0: No such file or directory
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
...
(--) Assigning device section with no busID to primary device
(--) Chipset generic found
(II) resource ranges after probing:
...
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading / usr/ lib/ xorg/ modules/ / libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading / usr/ lib/ xorg/ modules/ / libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8128 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Q33/ Q35/ G33 Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Q33/ Q35/ G33 Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
	"Builtin Default vesa Screen 0" for depth/ fbbpp 16/ 16
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SYN  Model: 4b  Serial#: 235
(II) VESA(0): Year: 2007  Week: 40
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): DFP 1.x compatible TMDS
(II) VESA(0): Max H-Image Size [cm]: horiz.: 104  vert.: 58
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/ Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): GTF timings supported
(II) VESA(0): redX: 0.652 redY: 0.331   greenX: 0.276 greenY: 0.597
(II) VESA(0): blueX: 0.145 blueY: 0.066   whiteX: 0.285 whiteY: 0.293
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) VESA(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 148.5 MHz   Image Size:  1040 x 580 mm
(II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 74.2 MHz   Image Size:  1040 x 580 mm
(II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) VESA(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) VESA(0): Ranges: V min: 21  V max: 85 Hz, H min: 25  H max: 84 kHz, PixClock max 160 MHz
(II) VESA(0): Monitor name: 247FHD-T11
(II) VESA(0): Number of EDID sections to follow: 1
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff004f2e4b00eb000000
(II) VESA(0): 	2811010381683a782b3f00a754469825
(II) VESA(0): 	11494b254b0081c081809500a940b300
(II) VESA(0): 	010101010101023a801871382d40582c
(II) VESA(0): 	450010444200001e011d8018711c1620
(II) VESA(0): 	582c250010444200009e000000fd0015
(II) VESA(0): 	55195410000a202020202020000000fc
(II) VESA(0): 	003234374648442d5431310a20200181
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) VESA(0): Modeline "1600x1200"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
(II) VESA(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) VESA(0): Modeline "1920x1080"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
(II) VESA(0): Modeline "1920x540"   74.25  1920 2008 2052 2200  540 542 547 562 interlace +hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 161 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 162 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 14b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 15a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 107 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006018
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 127 64KB banks (8128kB)
(II) VESA(0): Builtin Default Monitor: Using hsync range of 25.00-84.00 kHz
(II) VESA(0): Builtin Default Monitor: Using vrefresh range of 21.00-85.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(--) VESA(0): Virtual size is 1600x1200 (pitch 1600)
(**) VESA(0): *Built-in mode "1600x1200"
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(++) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (11a)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (117)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading / usr/ lib/ xorg/ modules/ / libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading / usr/ lib/ xorg/ modules/ / libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) UnloadModule: "i810"
(II) Unloading / usr/ lib/ xorg/ modules/ drivers/ / i810_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading / usr/ lib/ xorg/ modules/ drivers/ / fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading / usr/ lib/ xorg/ modules/ linux/ / libfbdevhw.so
(II) UnloadModule: "vga"
(II) Unloading / usr/ lib/ xorg/ modules/ drivers/ / vga_drv.so
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
...
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading / usr/ lib/ xorg/ modules/ / libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8128 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Q33/ Q35/ G33 Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Q33/ Q35/ G33 Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xe0000000, size: 0x7f0000
(II) VESA(0): Splitting WC range: base: 0xe0400000, size: 0x3f0000
(II) VESA(0): Splitting WC range: base: 0xe0600000, size: 0x1f0000
(II) VESA(0): Splitting WC range: base: 0xe0700000, size: 0xf0000
(II) VESA(0): Splitting WC range: base: 0xe0780000, size: 0x70000
(II) VESA(0): Splitting WC range: base: 0xe07c0000, size: 0x30000
(==) VESA(0): Write-combining range (0xe07e0000,0x10000)
(==) VESA(0): Write-combining range (0xe07c0000,0x30000)
(==) VESA(0): Write-combining range (0xe0780000,0x70000)
(==) VESA(0): Write-combining range (0xe0700000,0xf0000)
(WW) VESA(0): Failed to set up write-combining range (0xe0600000,0x1f0000)
(WW) VESA(0): Failed to set up write-combining range (0xe0400000,0x3f0000)
(WW) VESA(0): Failed to set up write-combining range (0xe0000000,0x7f0000)
(II) VESA(0): virtual address = 0xb7165000,
	physical address = 0xe0000000, size = 8323072
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading / usr/ lib/ xorg/ modules/ extensions/ / libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/ dev/ input/ mice"
(--) <default pointer>: Device: "/ dev/ input/ mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: Core Pointer
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) <default keyboard>: Core Keyboard
(**) Option "Protocol" "standard"
(**) <default keyboard>: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) <default keyboard>: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) <default keyboard>: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) <default keyboard>: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) <default keyboard>: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "<default keyboard>" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/ 2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/ usr/ share/ fonts/ X11/ misc" refcount is 2, should be 1; fixing.



---

