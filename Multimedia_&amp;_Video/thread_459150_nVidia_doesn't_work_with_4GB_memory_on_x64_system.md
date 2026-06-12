---
title: "nVidia doesn't work with 4GB memory on x64 system"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by pcraven on 2007-05-30
I can't start x-windows with 4GB of memory or more. I can run fine with 3 GB or 2 GB of memory. But if I increase my system to 4 GB of RAM under Fiesty x64, I can't start x-windows. I'm running nVidia drivers with a GeForce 7600.

I see using Google there have been issues with increasing memory past 4 GB, but most of those have been related to running under Vista.

Here's my log. 

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux craven-desktop 2.6.20-16-generic #2 SMP Wed May 23 00:30:47 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 30 11:11:29 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HP LP2065"
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GS]"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 147b,240a rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:1a:0: chip 10b9,5249 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 10b9,5237 card 147b,240a rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:1c:1: chip 10b9,5237 card 147b,240a rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:1c:2: chip 10b9,5237 card 147b,240a rev 03 class 0c,03,10 hdr 80
(II) PCI: 00:1c:3: chip 10b9,5239 card 147b,240a rev 01 class 0c,03,20 hdr 80
(II) PCI: 00:1d:0: chip 10b9,5461 card 147b,240a rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1e:0: chip 10b9,1575 card 147b,240a rev 00 class 06,01,00 hdr 80
(II) PCI: 00:1e:1: chip 10b9,7101 card 147b,240a rev 00 class 06,80,00 hdr 80
(II) PCI: 00:1f:0: chip 10b9,5229 card 147b,240a rev c8 class 01,01,fa hdr 80
(II) PCI: 00:1f:1: chip 10b9,5288 card 147b,240a rev 10 class 01,01,85 hdr 80
(II) PCI: 01:00:0: chip 10de,0392 card 1682,2221 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:11:0: chip 10ec,8169 card 147b,240a rev 10 class 02,00,00 hdr 00
(II) PCI: 02:12:0: chip 104c,8023 card 147b,240a rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdeffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:26:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:30:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xdc000000/24, 0xc0000000/28, 0xdd000000/24, I/O @ 0xef00/7
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
(II) PCI I/O resource overlap reduced 0x0000ff00 from 0x0000ff1f to 0x0000feff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[1] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[2] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[3] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[4] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[5] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[6] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[13] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[14] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[15] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[17] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[18] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[1] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[2] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[3] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[4] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[5] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[6] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[13] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[14] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[15] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[17] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[18] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
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
	[4] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[5] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[6] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[8] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[9] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[10] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[25] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[26] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
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
	compiled for 4.0.2, module version = 1.0.9755
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
	compiled for 4.0.2, module version = 1.0.9755
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:18:52 PST 2007
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
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
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
	[4] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[5] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[6] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[8] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[9] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[10] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[25] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[26] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[5] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[6] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[8] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[9] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[10] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[22] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[23] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[24] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[26] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[28] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[29] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     HP LP2065 (DFP-0)
(--) NVIDIA(0):     HP LP2065 (DFP-1)
(--) NVIDIA(0): HP LP2065 (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): HP LP2065 (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): HP LP2065 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): HP LP2065 (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select,nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 3200 x 1200
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfef8000 - 0xdfefbfff (0x4000) MX[B]
	[8] -1	0	0xdfefe000 - 0xdfefe7ff (0x800) MX[B]
	[9] -1	0	0xdfeff000 - 0xdfeff0ff (0x100) MX[B]
	[10] -1	0	0xdfffb000 - 0xdfffb3ff (0x400) MX[B]
	[11] -1	0	0xdfff4000 - 0xdfff7fff (0x4000) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffc0ff (0x100) MX[B]
	[13] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[14] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[15] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[26] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[27] -1	0	0x0000fa00 - 0x0000fa03 (0x4) IX[B]
	[28] -1	0	0x0000fb00 - 0x0000fb07 (0x8) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[30] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe0f (0x10) IX[B]
	[32] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[33] -1	0	0x0000ff00 - 0x0000feff (0x0) IX[B]O
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Setting mode "nvidia-auto-select,nvidia-auto-select"
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) Loading extension NV-GLX
```

---

### Post by blazercist on 2007-05-30
ewww, crappy nvidia driver... whered you get it from?  Is this the Proprietary one or the Free one?

---

### Post by dabl on 2007-05-30
My GeF 7900GS works fine in Ubuntu Feisty 64-bit with 4GB of RAM, including overclocking and Beryl. It could be something specific related to your GeF 7600.  How did you install the driver?  For the 64-bit system, I used Envy (meaning I just got to re-use it in text mode the other day after the upgrade broke it).

On the same hardware I also run a 32-bit Kubuntu Feisty, but of course it only sees 2GB of the RAM.

---

### Post by pcraven on 2007-05-30
I use one of the 'restricted drivers' for Ubuntu, nvidia-glx-new. I think I've also tried nvidia-glx, but I'll have to go back and check for certain.

I had Beryl working with Edgy, but it doesn't work with Fiesty on two different systems I've got. Specifically, Emerald doesn't work and I lose my window decorators.

The free driver doesn't recognize my LCD panel size correctly so I get stuck at low res. Plus I can't use TwinView, although Xinerama would work.

---

### Post by tseliot on 2007-05-31
Try Envy:
use the "uninstall" function and then the "install" function

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by gtfyre on 2007-05-31
Did you enable memory remap in your bios?

---

### Post by pcraven on 2007-06-01
I tried envy. I ran it from the text console. The uninstall script ran ok. The install script said the build failed. The errors were in the build log. Unfortunately the build log was mostly empty:

```
Build log starting, file: /var/cache/modass/nvidia-kernel-source.buildlog.2.6.20-16-generic.1180707581
Date: Fri, 01 Jun 2007 09:19:41 -0500

```

---

### Post by pcraven on 2007-06-01
I've got an Abit At8 with a zillion options for memory, but nothing about 'memory remap'.

---

