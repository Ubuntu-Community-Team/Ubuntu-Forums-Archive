---
title: "Xorg crash with Nvidia driver"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Squishy on 2007-05-27
I installed the latest nvidia drivers using envy (0.9.4-0ubuntu6).

When I restart x or reboot it crashes and gives me a backtrace. I couldn't find anything about it, so I turn to the forums.

```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]

```

Logs and other info:

gdm log:
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux zoidberg 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 27 11:46:33 2007
(==) Using config file: "/etc/X11/xorg.conf"

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

```

xorg log

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux zoidberg 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 27 11:46:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
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
(II) PCI: 00:00:0: chip 1106,0282 card 1043,80a3 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7282 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 1102,0002 card 1102,8026 rev 07 class 04,01,00 hdr 80
(II) PCI: 00:0d:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810d rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,02e1 card 1682,2247 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xfbffffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf8ffffff (0x19000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7600 GS rev 162, Mem @ 0xfb000000/24, 0xe0000000/28, 0xfa000000/24, BIOS @ 0xf9f00000/17
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
(II) PCI Memory resource overlap reduced 0xde000000 from 0xdfffffff to 0xddffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[1] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[2] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[3] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[4] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[8] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[1] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[2] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[3] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[4] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[5] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[6] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[8] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	[4] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[5] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[6] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[7] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.03  Thu Apr  5 02:28:49 PDT 2007
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
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.03  Thu Apr  5 01:55:08 PDT 2007
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
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
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
	[4] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[5] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[6] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[7] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[5] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[6] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[7] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[17] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.96
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     IBM (CRT-1)
(--) NVIDIA(0): IBM (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf9c00000 - 0xf9c000ff (0x100) MX[B]
	[8] -1	0	0xf9d00000 - 0xf9d000ff (0x100) MX[B]
	[9] -1	0	0xde000000 - 0xddffffff (0x0) MX[B]O
	[10] -1	0	0xf9f00000 - 0xf9f1ffff (0x20000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[20] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[21] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

```


xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Apr  5 02:10:21 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 64.0
    VertRefresh     50.0 - 105.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "TripleBuffer" "true"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

If anyone needs more information, I'll be happy to provide it.

---

### Post by simonn on 2007-05-28
gdm/X had been crashing on me occasionally for a while and I thought it was beryl related. Anyway, had got bored of wobbley windows, so had stopped using beryl and when gdm restarted twice within a two hour period on Saturday during a long programming session, I thought I better trouble shoot it.

In syslog I got:

```

gdm[4956]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

```

ls -lt /var/log/gdm, there were a logs,  :0.log.2 and  :0.log.3 which stopped at the time of the crashes. Looking inside them:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv000669X+0xd2) [0xb7192c8a]

```

Looked like a bug in the nvidia drivers, so I downgraded them to 1.0-9746 and have not had a problem since (touch wood). And, I used the PC ALL Sat and Sun.

My backtrace is EXACTLY the same as your's, memory locations and all, so... looks like a nvidia driver bug.

---

### Post by Squishy on 2007-05-28
> **simonn said:**
> Looked like a bug in the nvidia drivers, so I downgraded them to 1.0-9746 and have not had a problem since (touch wood). And, I used the PC ALL Sat and Sun.

My backtrace is EXACTLY the same as your's, memory locations and all, so... looks like a nvidia driver bug.
I only get that backtrace when I use the 100.14.03 version, which the latest unstable version of envy installs. If I use other drivers I get a lockup and can't even get to a tty. It just hangs the whole system and doesn't even write a Xorg.0.log

I can get rid of the backtrace by downgrading, but getting lockups instead isn't a good improvement.

So I thought I was making progress getting my new card to run with 3D, but alas.

The card is a GeForce 7600 GS.

---

### Post by tseliot on 2007-05-28
> **Squishy said:**
> I only get that backtrace when I use the 100.14.03 version, which the latest unstable version of envy installs. If I use other drivers I get a lockup and can't even get to a tty. It just hangs the whole system and doesn't even write a Xorg.0.log

I can get rid of the backtrace by downgrading, but getting lockups instead isn't a good improvement.

So I thought I was making progress getting my new card to run with 3D, but alas.

The card is a GeForce 7600 GS.

I think you should report your problems directly to Nvidia (on its forums):
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by Squishy on 2007-05-28
> **tseliot said:**
> I think you should report your problems directly to Nvidia (on its forums):
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)
[Done](http://www.nvnews.net/vbulletin/showthread.php?t=92262), will report back if anything usefull comes out of it.

---

### Post by Squishy on 2007-05-29
The problem lies with agp, either agpgart or nvagp, because when I set "option nvagp 0" in xorg.conf it start just fine. Although I don't AGP now, so glxgears  only gets 2000 - 2200 fps it still works.

Is this a bug or should I fiddly around with my bios settings for agp?

---

### Post by simonn on 2007-05-30
Have a look at my previous post [http://ubuntuforums.org/showpost.php?p=1352092&postcount=6](http://ubuntuforums.org/showpost.php?p=1352092&postcount=6).

---

### Post by Squishy on 2007-05-30
> **simonn said:**
> Have a look at my previous post [http://ubuntuforums.org/showpost.php?p=1352092&postcount=6](http://ubuntuforums.org/showpost.php?p=1352092&postcount=6).

Thanks, but that didn't help me much.

```

$ cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.        

```

```

$ lsmod | grep agp
amd64_agp              13700  1 
agpgart                35400  2 nvidia,amd64_agp

```

I tried blacklisting the amd64_agp, then I just get the disabled without the extra dmesg text.

```

$ dmesg | grep -i agp
[   42.072085] Linux agpgart interface v0.102 (c) Dave Jones
[   42.465648] agpgart: Detected AGP bridge 0
[   42.467053] agpgart: AGP aperture is 32M @ 0xd0000000
[   58.645919] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   58.646044] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   58.646201] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   64.595618] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   64.595908] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   64.596168] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   69.930778] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   69.930966] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   69.931147] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

:(

---

### Post by xzero1 on 2007-06-07
About 3 hrs ago I updated my bios. I found that the system would boot up until switching resolutions for the password screen. Suspecting the video driver, I booted from the live cd and added the nvidia restricted driver. After restarting X server the screen was blank.  This was working before! After examining the system logs (via the live cd). I noticed a problem with the agp aperture. Changing that in the bios from 32MB to 64MB got me back up and running. If this helps then there may be a bug associated with the nvidia driver. Good luck.

---

