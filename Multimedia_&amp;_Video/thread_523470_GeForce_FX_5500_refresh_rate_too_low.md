---
title: "GeForce FX 5500 refresh rate too low"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by Dubbayoo on 2007-08-11
I have just installed a GeForce FX 5500 on Feisty with a Viewsonic PF790 monitor. I use 1400x1050 resolution but I cannot get a refresh rate higher than 57 Hz. I know the monitor will do 72 Hz at 1600x1200 so that isn't the issue. 

I have tried several modelines and that isn't improving things. Anyone else using this card? 

[B]
Here is my X.log[/B]



```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 11 18:43:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PF790"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5500]"
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
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 8086,2531 card 15d9,2980 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2533 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 15d9,2980 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 15d9,2980 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 15d9,2980 rev 04 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 15d9,2980 rev 04 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:1f:0: chip 8086,1360 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 03:00:0: chip 8086,1161 card 8086,1161 rev 01 class 08,00,20 hdr 80
(II) PCI: 04:01:0: chip 8086,1229 card 1014,305c rev 08 class 02,00,00 hdr 00
(II) PCI: 04:02:0: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 04:02:1: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 04:02:2: chip 1033,00e0 card 0e55,2928 rev 04 class 0c,03,20 hdr 00
(II) PCI: 04:03:0: chip 1000,000c card 1de1,3907 rev 01 class 01,00,00 hdr 00
(II) PCI: 04:04:0: chip 8086,1229 card 8086,100c rev 08 class 02,00,00 hdr 00
(II) PCI: 04:07:0: chip 1102,0004 card 1102,0053 rev 03 class 04,01,00 hdr 80
(II) PCI: 04:07:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 04:07:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x70000000 - 0x702fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (2:31:0), (2,3,3), BCTRL: 0x8006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xf4000000/24, 0xe0000000/28
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf3ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[1] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[2] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[3] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[4] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[5] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[6] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[7] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[8] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[9] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[10] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[17] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[18] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[1] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[2] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[3] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[4] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[5] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[6] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[7] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[8] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[9] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[10] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[17] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[18] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
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
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[23] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[24] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[27] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
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
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9639  Mon Apr 16 20:21:54 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
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
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[23] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[24] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[27] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[25] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[26] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[27] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[28] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[30] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1400x1050"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1400 x 1050
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(**) NVIDIA(0): DPI set to (97, 96); computed from "DisplaySize" Monitor
(**) NVIDIA(0):     section option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[1] 0	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[7] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[8] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[9] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[10] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[11] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[12] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[13] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[14] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[15] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[16] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[17] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[28] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[29] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[30] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[31] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[32] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000280, 0x00000624)
(WW) NVIDIA(0): WAIT (0, 6, 0x0000, 0x00000624, 0x00000624)
(II) NVIDIA(0): Setting mode "1400x1050"
(WW) NVIDIA(0): WAIT (0, 3, 0x8000, 0x00000d3c, 0x00000d3c)
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000d7c, 0x00000d7c)
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
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
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000e88, 0x00000e88)
(II) NVIDIA(0): Setting mode "1400x1050_60"
(WW) NVIDIA(0): WAIT (2, 3, 0x8000, 0x00001200, 0x00001610)
(WW) NVIDIA(0): WAIT (0, 3, 0x8000, 0x00001610, 0x00001610)
(WW) NVIDIA(0): WAIT (0, 11, 0x8000, 0x00001630, 0x00001630)
(WW) NVIDIA(0): WAIT (0, 2, 0x8000, 0x00001670, 0x00001670)
(II) 3rd Button detected: disabling emulate3Button
```

---

### Post by tseliot on 2007-08-12
what refresh rate does nvidia-settings report?

---

