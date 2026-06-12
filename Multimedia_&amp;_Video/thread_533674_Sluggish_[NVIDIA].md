---
title: "Sluggish [NVIDIA]"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by leveliv on 2007-08-24
k well I used Envy to install my Nvidia drivers yesterday but instead of a total freeze like I used to have it just becomes Horribly Sluggish...like I can move the mouse but it's like there is a Huge Pressure on it...like its doing something really CPU heavy. It's not a total freeze up, My Music gets all choppy and the mouse skips along...anyone else had this? I have a Geforce 6200TC

---

### Post by tseliot on 2007-08-24
can you post your /var/log/Xorg.0.log ?

---

### Post by leveliv on 2007-08-24
here

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux lvliv-ubuntubox 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 24 15:47:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a24 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a24 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a24 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a24 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a24 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a24 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a24 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a24 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a25 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0161 card 1043,81ba rev a1 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a24 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 103c,2a24 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
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
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[13] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[14] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[13] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[14] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[20] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[19] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[20] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[26] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[27] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[29] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[30] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[31] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.0.0
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
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	Quadro FX 5600, Quadro FX 4600
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 6200 TurboCache(TM) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[19] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[20] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[26] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[27] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[29] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[30] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[31] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[22] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[29] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[30] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[32] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[34] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): Initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) NV(0): Bad V_BIOS checksum
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6200 TurboCache(TM)"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xFA000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: SAM  Model: 40d9  Serial#: 1346842937
(II) NV(0): Year: 2001  Week: 15
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) NV(0): Gamma: 2.28
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.638 redY: 0.325   greenX: 0.276 greenY: 0.596
(II) NV(0): blueX: 0.143 blueY: 0.066   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) NV(0): #5: hsize: 1024  vsize 768  refresh: 100  vid: 26721
(II) NV(0): #6: hsize: 2048  vsize 1536  refresh: 60  vid: 16609
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 157.5 MHz   Image Size:  352 x 264 mm
(II) NV(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 210 MHz
(II) NV(0): Monitor name: S/M 950p
(II) NV(0): Serial No: H3NR404290
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004c2dd94039314750
(II) NV(0): 	0f0b01020f241b80eb5e89a353469824
(II) NV(0): 	11484cffff803159455961598199a94f
(II) NV(0): 	6168e1400101863d00c05100304040a0
(II) NV(0): 	130060081100001e000000fd0032a01e
(II) NV(0): 	6015000a202020202020000000fc0053
(II) NV(0): 	2f4d20393530700a20202020000000ff
(II) NV(0): 	0048334e523430343239300a202000a7
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) NV(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   35.50  720 738 846 900  400 421 423 449 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
(II) NV(0): Modeline "1600x1200"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync
(II) NV(0): Modeline "1024x768"  112.25  1024 1096 1200 1376  768 771 775 816 -hsync +vsync
(II) NV(0): Modeline "2048x1536"  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(--) NV(0): VideoRAM: 16384 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (vrefresh out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "720x400" (vrefresh out of range)
(II) NV(0): Not using driver mode "720x400" (vrefresh out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using driver mode "832x624" (vrefresh out of range)
(II) NV(0): Not using driver mode "800x600" (vrefresh out of range)
(II) NV(0): Not using driver mode "800x600" (vrefresh out of range)
(II) NV(0): Not using driver mode "1152x864" (hsync out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "800x600" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using driver mode "1600x1200" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "2048x1536" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): Display dimensions: (360, 270) mm
(**) NV(0): DPI set to (72, 72)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[8] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[25] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[32] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[33] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[35] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[36] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[37] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd0000000,0x1000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		16 256x256 slots
		6 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
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
```


Mind you I have disable the nvidia drivers to post this..I also have one that is label 0.log.old

---

### Post by tseliot on 2007-08-24
the driver wasn't installed properly.

1) post your /var/log/envy-installer.log

2) the output of this command:
```
sudo aptitude search nvidia
```

---

### Post by leveliv on 2007-08-24
```
python pulse.py nvidia
root@lvliv-ubuntubox:/usr/share/envy# python pulse.py nvidia 
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce 6200 TurboCache(TM)
Your graphic card is supported by the latest driver
ENVY: The following packages are not installed:
linux-headers-`uname -r`

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1.0-dev libaudio-dev libcairo2-dev libcupsys2-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev
  libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev
  libjpeg62-dev liblcms1-dev liblzo-dev libmng-dev libopencdk8-dev
  libpango1.0-dev libpng12-dev libpopt-dev libqt3-headers libsm-dev
  libtasn1-3-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev mesa-common-dev qt3-dev-tools x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgcrypt11-doc libglib2.0-doc gnutls-doc libgtk2.0-doc
  libpango1.0-doc libqt3-i18n qt3-doc mailx
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  kernel-wedge libatk1.0-dev libaudio-dev libcairo2-dev libcupsys2-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev
  libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev
  libgpg-error-dev libgtk2.0-dev libice-dev libjpeg62-dev liblcms1-dev
  liblzo-dev libmng-dev libopencdk8-dev libpango1.0-dev libpng12-dev
  libpopt-dev libqt3-headers libqt3-mt-dev libsm-dev libtasn1-3-dev libx11-dev
  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev libxtst-dev libxxf86misc-dev libxxf86vm-dev
  mesa-common-dev qt3-dev-tools sharutils x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xf86misc-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 61 newly installed, 0 to remove and 8 not upgraded.
Need to get 20.5MB of archives.
After unpacking, 64.7MB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-core-dev 7.0.10-1 [86.3kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libfreetype6-dev 2.2.1-5ubuntu1.1 [640kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libice-dev 2:1.0.3-1build1 [55.9kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libsm-dev 2:1.0.2-1build1 [25.6kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxau-dev 1:1.0.3-1 [15.5kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxdmcp-dev 1:1.0.2-1 [19.8kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-input-dev 1.4.1-1 [15.4kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-kb-dev 1.0.3-2ubuntu1 [27.0kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main xtrans-dev 1.0.3-1 [69.2kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libx11-dev 2:1.1.1-1ubuntu3 [8685kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libpng12-dev 1.2.15~beta5-1ubuntu1 [172kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libqt3-headers 3:3.3.8really3.3.7-0ubuntu5.1 [355kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main qt3-dev-tools 3:3.3.8really3.3.7-0ubuntu5.1 [1237kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libqt3-mt-dev 3:3.3.8really3.3.7-0ubuntu5.1 [48.6kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-render-dev 2:0.9.2-4ubuntu1 [6960B]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxrender-dev 1:0.9.1-3 [24.4kB]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-xext-dev 7.0.2-5ubuntu1 [42.2kB]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-fixes-dev 1:4.0-0.1ubuntu2 [5662B]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxfixes-dev 1:4.0.3-1 [12.1kB]
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxcursor-dev 1:1.1.8-1 [30.6kB]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxext-dev 2:1.0.3-1build1 [81.5kB]
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libexpat1-dev 1.95.8-3.4build1 [129kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main zlib1g-dev 1:1.2.3-13ubuntu4 [407kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libfontconfig1-dev 2.4.2-1ubuntu1 [344kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxft-dev 2.1.12-1 [60.7kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxi-dev 2:1.1.0-1build1 [67.7kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxinerama-dev 2:1.0.1-4build1 [4196B]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxmu-headers 2:1.0.2-1ubuntu2 [16.2kB]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-randr-dev 1.2.1-1 [28.6kB]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxrandr-dev 2:1.2.0-3ubuntu1 [27.5kB]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxt-dev 1:1.0.5-1 [482kB]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-record-dev 1.13.2-4ubuntu1 [6022B]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxtst-dev 2:1.0.1-3build1 [8978B]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-xf86misc-dev 0.9.2-4ubuntu1 [5614B]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxxf86misc-dev 1:1.0.1-2 [9594B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main x11proto-xf86vidmode-dev 2.2.2-4ubuntu1 [6596B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxxf86vm-dev 1:1.0.1-2 [14.1kB]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main kernel-wedge 2.29ubuntu2 [40.0kB]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libglib2.0-dev 2.12.11-0ubuntu1 [536kB]
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libatk1.0-dev 1.18.0-0ubuntu1 [112kB]
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libcairo2-dev 1.4.2-0ubuntu1 [507kB]
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libgpg-error-dev 1.4-2build1 [33.7kB]
Get:44 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libgcrypt11-dev 1.2.3-2build1 [248kB]
Get:45 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libtasn1-3-dev 0.3.6-2build1 [310kB]
Get:46 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libpopt-dev 1.10-3build1 [38.3kB]
Get:47 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libopencdk8-dev 0.5.9-2build1 [122kB]
Get:48 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main liblzo-dev 1.08-3 [109kB]
Get:49 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libgnutls-dev 1.4.4-3build1 [358kB]
Get:50 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libcupsys2-dev 1.2.8-0ubuntu8 [139kB]
Get:51 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main mesa-common-dev 6.5.2-3ubuntu8 [175kB]
Get:52 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main libgl1-mesa-dev 6.5.2-3ubuntu8 [25.0kB]
Get:53 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main libglu1-mesa-dev 6.5.2-3ubuntu8 [257kB]
Get:54 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libpango1.0-dev 1.16.2-0ubuntu1 [355kB]
Get:55 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libgtk2.0-dev 2.10.11-0ubuntu3 [2590kB]
Get:56 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libjpeg62-dev 6b-13 [185kB]    
Get:57 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main liblcms1-dev 1.15-1 [135kB]
Get:58 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libmng-dev 1.0.9-1 [285kB]
Get:59 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxmu-dev 2:1.0.2-1ubuntu2 [50.6kB]
Get:60 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libaudio-dev 1.8-4 [501kB]
Get:61 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main sharutils 1:4.2.1-15 [111kB]   
Fetched 20.5MB in 50s (408kB/s)
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 127012 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.10-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.3-1build1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.2-1build1_i386.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.1-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.3-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.1-1ubuntu3_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.1-3_i386.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-0.1ubuntu2_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.8-1_i386.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-1build1_i386.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3.4build1_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-13ubuntu4_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.2.1-5ubuntu1.1_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.4.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-1_i386.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.0-1build1_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-4build1_i386.deb) ...
Selecting previously deselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.2-1ubuntu2_all.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-1_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.0-3ubuntu1_i386.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-1_i386.deb) ...
Selecting previously deselected package x11proto-record-dev.
Unpacking x11proto-record-dev (from .../x11proto-record-dev_1.13.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxtst-dev.
Unpacking libxtst-dev (from .../libxtst-dev_2%3a1.0.1-3build1_i386.deb) ...
Selecting previously deselected package x11proto-xf86misc-dev.
Unpacking x11proto-xf86misc-dev (from .../x11proto-xf86misc-dev_0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86misc-dev.
Unpacking libxxf86misc-dev (from .../libxxf86misc-dev_1%3a1.0.1-2_i386.deb) ...
Selecting previously deselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.0.1-2_i386.deb) ...
Selecting previously deselected package kernel-wedge.
Unpacking kernel-wedge (from .../kernel-wedge_2.29ubuntu2_all.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.4.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgpg-error-dev.
Unpacking libgpg-error-dev (from .../libgpg-error-dev_1.4-2build1_i386.deb) ...
Selecting previously deselected package libgcrypt11-dev.
Unpacking libgcrypt11-dev (from .../libgcrypt11-dev_1.2.3-2build1_i386.deb) ...
Selecting previously deselected package libtasn1-3-dev.
Unpacking libtasn1-3-dev (from .../libtasn1-3-dev_0.3.6-2build1_i386.deb) ...
Selecting previously deselected package libpopt-dev.
Unpacking libpopt-dev (from .../libpopt-dev_1.10-3build1_i386.deb) ...
Selecting previously deselected package libopencdk8-dev.
Unpacking libopencdk8-dev (from .../libopencdk8-dev_0.5.9-2build1_i386.deb) ...
Selecting previously deselected package liblzo-dev.
Unpacking liblzo-dev (from .../liblzo-dev_1.08-3_i386.deb) ...
Selecting previously deselected package libgnutls-dev.
Unpacking libgnutls-dev (from .../libgnutls-dev_1.4.4-3build1_i386.deb) ...
Selecting previously deselected package libcupsys2-dev.
Unpacking libcupsys2-dev (from .../libcupsys2-dev_1.2.8-0ubuntu8_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.5.2-3ubuntu8_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.2-3ubuntu8_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.5.2-3ubuntu8_i386.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.16.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.10.11-0ubuntu3_i386.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-13_i386.deb) ...
Selecting previously deselected package liblcms1-dev.
Unpacking liblcms1-dev (from .../liblcms1-dev_1.15-1_i386.deb) ...
Selecting previously deselected package libmng-dev.
Unpacking libmng-dev (from .../libmng-dev_1.0.9-1_i386.deb) ...
Selecting previously deselected package libqt3-headers.
Unpacking libqt3-headers (from .../libqt3-headers_3%3a3.3.8really3.3.7-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libaudio-dev.
Unpacking libaudio-dev (from .../libaudio-dev_1.8-4_i386.deb) ...
Selecting previously deselected package qt3-dev-tools.
Unpacking qt3-dev-tools (from .../qt3-dev-tools_3%3a3.3.8really3.3.7-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package libqt3-mt-dev.
Unpacking libqt3-mt-dev (from .../libqt3-mt-dev_3%3a3.3.8really3.3.7-0ubuntu5.1_i386.deb) ...
Selecting previously deselected package sharutils.
Unpacking sharutils (from .../sharutils_1%3a4.2.1-15_i386.deb) ...
Setting up x11proto-core-dev (7.0.10-1) ...
Setting up libice-dev (1.0.3-1build1) ...
Setting up libsm-dev (1.0.2-1build1) ...
Setting up libxau-dev (1.0.3-1) ...
Setting up libxdmcp-dev (1.0.2-1) ...
Setting up x11proto-input-dev (1.4.1-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.3-1) ...
Setting up libx11-dev (1.1.1-1ubuntu3) ...
Setting up x11proto-render-dev (0.9.2-4ubuntu1) ...
Setting up libxrender-dev (0.9.1-3) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up x11proto-fixes-dev (4.0-0.1ubuntu2) ...
Setting up libxfixes-dev (4.0.3-1) ...
Setting up libxcursor-dev (1.1.8-1) ...
Setting up libxext-dev (1.0.3-1build1) ...
Setting up libexpat1-dev (1.95.8-3.4build1) ...

Setting up zlib1g-dev (1.2.3-13ubuntu4) ...
Setting up libfreetype6-dev (2.2.1-5ubuntu1.1) ...

Setting up libfontconfig1-dev (2.4.2-1ubuntu1) ...
Setting up libxft-dev (2.1.12-1) ...
Setting up libxi-dev (1.1.0-1build1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (1.0.1-4build1) ...
Setting up libxmu-headers (1.0.2-1ubuntu2) ...
Setting up x11proto-randr-dev (1.2.1-1) ...
Setting up libxrandr-dev (1.2.0-3ubuntu1) ...
Setting up libxt-dev (1.0.5-1) ...
Setting up x11proto-record-dev (1.13.2-4ubuntu1) ...
Setting up libxtst-dev (1.0.1-3build1) ...
Setting up x11proto-xf86misc-dev (0.9.2-4ubuntu1) ...
Setting up libxxf86misc-dev (1.0.1-2) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-4ubuntu1) ...
Setting up libxxf86vm-dev (1.0.1-2) ...
Setting up kernel-wedge (2.29ubuntu2) ...
Setting up libglib2.0-dev (2.12.11-0ubuntu1) ...
Setting up libatk1.0-dev (1.18.0-0ubuntu1) ...
Setting up libpng12-dev (1.2.15~beta5-1ubuntu1) ...
Setting up libcairo2-dev (1.4.2-0ubuntu1) ...
Setting up libgpg-error-dev (1.4-2build1) ...
Setting up libgcrypt11-dev (1.2.3-2build1) ...
Setting up libtasn1-3-dev (0.3.6-2build1) ...
Setting up libpopt-dev (1.10-3build1) ...
Setting up libopencdk8-dev (0.5.9-2build1) ...

Setting up liblzo-dev (1.08-3) ...
Setting up libgnutls-dev (1.4.4-3build1) ...
Setting up libcupsys2-dev (1.2.8-0ubuntu8) ...
Setting up mesa-common-dev (6.5.2-3ubuntu8) ...
Setting up libgl1-mesa-dev (6.5.2-3ubuntu8) ...
Setting up libglu1-mesa-dev (6.5.2-3ubuntu8) ...
Setting up libpango1.0-dev (1.16.2-0ubuntu1) ...
Setting up libgtk2.0-dev (2.10.11-0ubuntu3) ...
Setting up libjpeg62-dev (6b-13) ...
Setting up liblcms1-dev (1.15-1) ...
Setting up libmng-dev (1.0.9-1) ...
Setting up libqt3-headers (3.3.8really3.3.7-0ubuntu5.1) ...
Setting up libxmu-dev (1.0.2-1ubuntu2) ...
Setting up libaudio-dev (1.8-4) ...
Setting up qt3-dev-tools (3.3.8really3.3.7-0ubuntu5.1) ...
Setting up libqt3-mt-dev (3.3.8really3.3.7-0ubuntu5.1) ...
Setting up sharutils (4.2.1-15) ...

ENVY: The following packages will be removed:
nvidia-glx-new

ENVY: attempting to remove the packages
An installer has been detected
md5new: d41d8cd98f00b204e9800998ecf8427e
md5sumold: 3e76376b5f1a53e0c18694fa65691c75
ENVY ERROR: md5 Error! Trying to fetch the driver from the website
No installer detected
Download of the driver in progress, please wait
--17:32:09--  [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)
           => `NVIDIA-Linux-x86-100.14.11-pkg1.run'
Resolving us.download.nvidia.com... 204.1.5.178, 204.1.5.171
Connecting to us.download.nvidia.com|204.1.5.178|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,311,226 (15M) [application/octet-stream]
100%[====================================>] 15,311,226   522.95K/s    ETA 00:00

17:32:38 (520.91 KB/s) - `NVIDIA-Linux-x86-100.14.11-pkg1.run' saved [15311226/15311226]
md5new: 3e76376b5f1a53e0c18694fa65691c75
md5sumold: 3e76376b5f1a53e0c18694fa65691c75
Checking the Dependencies for the New Method
OK: All the packages are installed
dpkg-buildpackage: source package is linux-restricted-modules-2.6.20
dpkg-buildpackage: source version is 2.6.20-16
dpkg-buildpackage: source changed by Colin Watson <cjwatson@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.6.20-16
debian/rules clean
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
dh_testdir
dh_testroot
rm -f unpack-stamp build-stamp build-kernel-stamp \
                  modalias-patterns-stamp
rm -rf debian/build* debian/temp/
rm -f debian/vmware-*-kernel-modules-*.postinst
rm -f debian/vmware-*-kernel-modules-*.postrm
rm -f debian/linux-restricted-modules-[0-9]*.postinst
rm -f debian/linux-restricted-modules-*.postrm
rm -f debian/linux-restricted-modules-*.preinst
rm -f debian/linux-restricted-modules-*.prerm
rm -f debian/nic-restricted-modules-*.postinst
for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                 -dev.preinst .dirs .docs .examples .links.amd64 \
                 .links .override .postinst .postrm .preinst \
                 .prerm .README.Debian .reportbug .shlibs; \
                do rm -f debian/nvidia-glx$i debian/nvidia-glx-legacy$i debian/nvidia-glx-new$i; \
        done
rm -rf nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1; \
        rm -f nvidia-kernel-source.tar.gz nvidia-legacy-kernel-source.tar.gz \
                nvidia-new-kernel-source.tar.gz
rm -f fglrx-kernel-source.tar.gz
dh_clean `find debian/d-i/modules debian/d-i/firmware -type l 2>/dev/null`
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
rm -rf avm-download build-avm-stamp unpack-avm-stamp
rm -rf debian/nic-restricted-modules-*-di \
                   debian/nic-restricted-firmware-*-di
rm -f correct-lib-path
cp -f debian/control.stub debian/control
 debian/rules build
dh_testdir
if [ -e debian/build ]; then \
                mv debian/build debian/build.old; \
        fi
mkdir debian/build
mkdir -p debian/build/2.6.20-16-generic
if [ "1.0.100.14.11" = "1.0.9639" ]; then       \
                cd nvidia && sh ./NVIDIA-Linux-x86-1.0-9639-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv debian/build/2.6.20-16-generic/nv; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.9639/g" -e "s/@@NV_LEGACY@@//g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1:"  -e "s/@@NV_ALT@@//g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx$i; \
                done; \
        fi
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then  \
                cd nvidia && sh ./NVIDIA-Linux-x86-100.14.11-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-new/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-new/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-100.14.11-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv debian/build/2.6.20-16-generic/nv-new; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.100.14.11/g" -e "s/@@NV_LEGACY@@/-new/g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-100.14.11-pkg1:"  -e "s/@@NV_ALT@@/new/g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx-new$i; \
                done; \
        fi
Creating directory NVIDIA-Linux-x86-100.14.11-pkg1
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.11........
................................................................................
................................................................................
................................................................................
..............................
if [ "1.0.100.14.11" = "1.0.7185" ]; then       \
                cd nvidia && sh ./NVIDIA-Linux-x86-1.0-7185-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-legacy/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-legacy/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv debian/build/2.6.20-16-generic/nv-legacy; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.7185/g" -e "s/@@NV_LEGACY@@/-legacy/g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1:"  -e "s/@@NV_ALT@@/legacy/g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx-legacy$i; \
                done; \
        fi;
sed -e "s/@@KVERSION@@/$i/g;" debian/linux-restricted-modules.postinst \
                        > debian/linux-restricted-modules-2.6.20-16-generic.postinst; \
                sed -e "s/@@KVERSION@@/$i/g;" debian/linux-restricted-modules.postrm \
                        > debian/linux-restricted-modules-2.6.20-16-generic.postrm;
touch unpack-stamp
dh_testdir
touch build-stamp
touch unpack-avm-stamp
dh_testdir
touch build-avm-stamp
dh_testdir
#if [ "1.0.100.14.11" = "9639" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-generic/nv/nv-kernel.o nvidia \
                #> debian/build/2.6.20-16-generic/nv/modules.alias.override; \
        #fi
#if [ "1.0.100.14.11" = "100.14.11" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-generic/nv-new/nv-kernel.o nvidia_new \
                #> debian/build/2.6.20-16-generic/nv/modules.alias.override; \
        #fi
#if [ "1.0.100.14.11" = "7185" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-generic/nv-legacy/nv-kernel.o nvidia_legacy \
                #> debian/build/2.6.20-16-generic/nv/modules.alias.override; \
        #fi
touch modalias-patterns-stamp
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
 debian/rules binary
dh_testdir
dh_installchangelogs -i
dh_installchangelogs: I have no package to build
dh_fixperms -i
dh_fixperms: I have no package to build
dh_compress -i
dh_compress: I have no package to build
dh_installdeb -i
dh_installdeb: I have no package to build
dh_gencontrol -i
dh_gencontrol: I have no package to build
dh_md5sums -i
dh_md5sums: I have no package to build
dh_builddeb -i
dh_builddeb: I have no package to build
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
dh_testdir
dh_testroot
chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/debian/$f ; \
                done    ; \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian; \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv; \
                cp -r /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/* /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian; \
                set +e && for f in `ls /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary` ; do \
                        perl -p \
                        -e 's{#BASE_VERSION#}{1.0}g;' \
                        -e 's{#RELEASE#}{7185}g;' \
                        -e 's{#VERSION#}{1.0.7185}g;' \
                        -e 's{#UPSTREAMVERSION#}{1.0-7185}g;' \
                        -e 's{#URL#}{http://download.nvidia.com/XFree86/Linux-x86/1.0-7185/NVIDIA-Linux-x86-1.0-7185-pkg1.run}g' \
                        < /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/$f \
                        > /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/$f ; \
                        chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/$f ; \
                done; \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-legacy-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian; \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv; \
                cp -r /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/* /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian; \
                set +e && for f in `ls /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary` ; do \
                        perl -p \
                        -e 's{#BASE_VERSION#}{1.0}g;' \
                        -e 's{#RELEASE#}{100.14.11}g;' \
                        -e 's{#VERSION#}{1.0.100.14.11}g;' \
                        -e 's{#UPSTREAMVERSION#}{1.0-100.14.11}g;' \
                        -e 's{#URL#}{http://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run}g' \
                        < /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/$f \
                        > /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/$f ; \
                        chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/$f ; \
                done; \
                cp -al nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-new-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/nv-kernel.o
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/nv-misc.h
touch build-kernel-stamp
dh_testdir
dh_clean -k
dh_installdirs
install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/libXvMCNVIDIA.so.100.14.11                 \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/libXvMCNVIDIA.so.100.14.11; \
                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/include/GL/gl.h                                      \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/share/doc/nvidia-glx-new-dev/include/GL; \
                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/include/GL/glext.h                           \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/share/doc/nvidia-glx-new-dev/include/GL; \
                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/include/GL/glx.h                                     \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/share/doc/nvidia-glx-new-dev/include/GL; \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/include/GL/glxext.h ]; then                          \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/include/GL/glxext.h                          \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/share/doc/nvidia-glx-new-dev/include/GL; \
                        fi;                                                    \
                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libGL.so.100.14.11                               \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib;                          \
                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libGLcore.so.100.14.11                   \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib;                          \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libnvidia-cfg.so.100.14.11 ]; then                       \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libnvidia-cfg.so.100.14.11               \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib;                  \
                        fi;                                                    \
                        sed "s/__GENERATED_BY__/Ubuntu nvidia--newgraphics-drivers/"            \
                                nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib/" >  \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/lib/libGL.la;             \
                        if [ "i386" = "amd64" ]; then                          \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32              \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/lib32;            \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGL.so.100.14.11             \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;                \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGLcore.so.100.14.11         \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;                \
                                if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-cfg.so.100.14.11 ]; then     \
                                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-cfg.so.100.14.11 \
                                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;        \
                                fi;                                            \
                                sed "s/__GENERATED_BY__/Ubuntu nvidia--newgraphics-drivers/"    \
                                        nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGL.la |                                     \
                                        sed "s/__LIBGL_PATH__/\/usr\/lib32/" > \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/lib32/libGL.la;   \
                        fi;                                                    \
                        install nvidia/nvidia-glx-config                       \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/sbin;                 \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libnvidia-tls.so.100.14.11                               \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/;                 \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/tls/libnvidia-tls.so.100.14.11                   \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/tls/;                     \
                        if [ "i386" = "amd64" ]; then                          \
                                install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-tls.so.100.14.11             \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/;               \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/tls; \
                                install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/tls/libnvidia-tls.so.100.14.11         \
                                         /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/tls/;          \
                        fi;                                                    \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/modules/extensions/libglx.so.100.14.11     \
                                 /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/xorg/modules/;           \
install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.100.14.11 \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/xorg/modules/;    \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/tls_test                                         \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/nvidia;                   \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/tls_test_dso.so                                  \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/nvidia;                   \
                        install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/lintian/overrides;   \
                        install -m 0644 debian/nvidia-glx-new.override         \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/lintian/overrides/nvidia-glx-new; \
                        install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-bug-report.sh                              \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;                 \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-settings.1.gz ]; then          \
                                install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-settings                   \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;         \
                                install -m 644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-settings.1.gz   \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/man/man1/;      \
                        fi;                                                    \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz ]; then           \
                                install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-xconfig                    \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;         \
                                install -m 644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz    \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/man/man1/;      \
                        fi;                                                    \
                        install /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new.reportbug                 \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/bug/nvidia-glx-new/script; \
                fi;
install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32           \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy-dev/usr/lib32;         \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGL.so.1.0.7185               \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;             \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGLcore.so.1.0.7185           \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;             \
                                if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-cfg.so.1.0.7185 ]; then       \
                                        install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-cfg.so.1.0.7185 \
                                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;     \
                                fi;                                            \
                                sed "s/__GENERATED_BY__/Ubuntu nvidia--legacygraphics-drivers/" \
                                        nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGL.la |                                      \
                                        sed "s/__LIBGL_PATH__/\/usr\/lib32/" > \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy-dev/usr/lib32/libGL.la;        \
                        fi;                                                    \
                        install nvidia/nvidia-glx-config                       \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/sbin;                      \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib/libnvidia-tls.so.1.0.7185                         \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/;                      \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib/tls/libnvidia-tls.so.1.0.7185                     \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/tls/;                  \
                        if [ "i386" = "amd64" ]; then                          \
                                install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-tls.so.1.0.7185               \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/;            \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/tls;      \
                                install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/tls/libnvidia-tls.so.1.0.7185           \
                                         /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/tls/;               \
                        fi;                                                    \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/X11R6/lib/modules/extensions/libglx.so.1.0.7185       \
                                 /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/xorg/modules/;                \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/tls_test                                          \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/nvidia;                        \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/tls_test_dso.so                                   \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/nvidia;                        \
                        install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/lintian/overrides;        \
                        install -m 0644 debian/nvidia-glx-legacy.override      \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/lintian/overrides/nvidia-glx-legacy; \
                        install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-bug-report.sh                               \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;                      \
                        if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-settings.1.gz ]; then           \
                                install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-settings                    \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;              \
                                install -m 644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-settings.1.gz    \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/man/man1/;   \
                        fi;                                                    \
                        if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz ]; then            \
                                install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-xconfig                     \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;              \
                                install -m 644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz     \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/man/man1/;   \
                        fi;                                                    \
                        install /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy.reportbug                      \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/bug/nvidia-glx-legacy/script; \
                fi;
#install
dh_testdir
dh_installchangelogs -s
dh_installdocs -s
dh_installexamples -s
dh_installman -s
dh_installinit -s
dh_link -s
# FIXME: Remove this when -legacy supports this library:
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                rm -f debian/nvidia-glx-legacy/usr/lib/libnvidia-cfg.so.1; \
                rm -f debian/nvidia-glx-legacy/usr/lib32/libnvidia-cfg.so.1; \
        fi;
dh_strip -s -X1.0.9639 -X1.0.7185 -Xtls_test
dh_compress -X.h -s
dh_fixperms -s
dh_installdeb -s
dh_shlibdeps -X'*tls*' -X'*lib32*' -X'*lib64*' -s \
                -l/usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx/usr/lib:/usr/share/envy/linux-restricted-modules-2.6.20/debian/xorg-driver-fglrx/usr/lib
# this is a dirty hack, but we don't want -glx-legacy to depend on -glx
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
        sed -i -e 's/, nvidia-glx//' debian/nvidia-glx-legacy.substvars ;\
        fi;
dh_gencontrol -s
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
# fglrx, nVidia and ACM build with different version numbers
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                dh_gencontrol -v -pnvidia-glx -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
                dh_gencontrol -v -pnvidia-glx-dev -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
                dh_gencontrol -v -pnvidia-kernel-source -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                dh_gencontrol -v -pnvidia-glx-new -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
                dh_gencontrol -v -pnvidia-glx-new-dev -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
                dh_gencontrol -v -pnvidia-new-kernel-source -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
        fi;
dpkg-gencontrol -pnvidia-glx-new -ldebian/changelog -isp -Tdebian/nvidia-glx-new.substvars -Pdebian/nvidia-glx-new -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-glx-new/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new/DEBIAN/control
dpkg-gencontrol -pnvidia-glx-new-dev -ldebian/changelog -isp -Tdebian/nvidia-glx-new-dev.substvars -Pdebian/nvidia-glx-new-dev -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-glx-new-dev/DEBIAN/control
chown 0:0 debian/nvidia-glx-new-dev/DEBIAN/control
dpkg-gencontrol -pnvidia-new-kernel-source -ldebian/changelog -isp -Tdebian/nvidia-new-kernel-source.substvars -Pdebian/nvidia-new-kernel-source -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-new-kernel-source/DEBIAN/control
        chown 0:0 debian/nvidia-new-kernel-source/DEBIAN/control
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                dh_gencontrol -v -pnvidia-glx-legacy -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-glx-legacy-dev -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-legacy-kernel-source -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
        fi;
dh_md5sums -s
dh_builddeb -s
dpkg-deb: building package `nvidia-glx-new' in `../nvidia-glx-new_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-glx-new-dev' in `../nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-new-kernel-source' in `../nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb'.
dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
OK: All the packages are installed
Selecting previously deselected package nvidia-new-kernel-source.
(Reading database ... 130631 files and directories currently installed.)
Unpacking nvidia-new-kernel-source (from nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-new-kernel-source (100.14.11+2.6.20-16) ...
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/nv-kernel.o
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/nv-misc.h
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
Creating symlink...
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Done!

fi;
        dpkg-gencontrol -pnvidia-glx-new -ldebian/changelog -isp -Tdebian/nvidia-glx-new.substvars -Pdebian/nvidia-glx-new -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
        chmod 644 debian/nvidia-glx-new/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new/DEBIAN/control
        dpkg-gencontrol -pnvidia-glx-new-dev -ldebian/changelog -isp -Tdebian/nvidia-glx-new-dev.substvars -Pdebian/nvidia-glx-new-dev -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
        chmod 644 debian/nvidia-glx-new-dev/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new-dev/DEBIAN/control
        dpkg-gencontrol -pnvidia-new-kernel-source -ldebian/changelog -isp -Tdebian/nvidia-new-kernel-source.substvars -Pdebian/nvidia-new-kernel-source -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
        chmod 644 debian/nvidia-new-kernel-source/DEBIAN/control
        chown 0:0 debian/nvidia-new-kernel-source/DEBIAN/control
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                dh_gencontrol -v -pnvidia-glx-legacy -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-glx-legacy-dev -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-legacy-kernel-source -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
        fi;
dh_md5sums -s
dh_builddeb -s
dpkg-deb: building package `nvidia-glx-new' in `../nvidia-glx-new_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-glx-new-dev' in `../nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-new-kernel-source' in `../nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb'.
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

OK: All the packages are installed
Selecting previously deselected package nvidia-new-kernel-source.
(Reading database ... 130631 files and directories currently installed.)
Unpacking nvidia-new-kernel-source (from nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-new-kernel-source (100.14.11+2.6.20-16) ...
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/nv-kernel.o
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/nv-misc.h
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Done!

Updated infos about 85 packages
Extracting the package tarball, /usr/src/nvidia-new-kernel-source.tar.gz, please wait...


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Building nvidia-new-kernel-source, step 2, please wait... &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                         
                         &#9474; rride                                                                   &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;                         
                         &#9474;                                                                         &#9474;
Version=100.14.11
        chmod 644 debian/nvidia-glx-new/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new/DEBIAN/control
        dpkg-gencontrol -pnvidia-glx-new-dev -ldebian/changelog -isp -Tdebian/nvidia-glx-new-dev.substvars -Pdebian/nvidia-glx-new-dev -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
        chmod 644 debian/nvidia-glx-new-dev/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new-dev/DEBIAN/control
        dpkg-gencontrol -pnvidia-new-kernel-source -ldebian/changelog -isp -Tdebian/nvidia-new-kernel-source.substvars -Pdebian/nvidia-new-kernel-source -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
        chmod 644 debian/nvidia-new-kernel-source/DEBIAN/control
        chown 0:0 debian/nvidia-new-kernel-source/DEBIAN/control
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                dh_gencontrol -v -pnvidia-glx-legacy -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-glx-legacy-dev -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-legacy-kernel-source -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
        fi;
dh_md5sums -s
dh_builddeb -s
dpkg-deb: building package `nvidia-glx-new' in `../nvidia-glx-new_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-glx-new-dev' in `../nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-new-kernel-source' in `../nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb'.
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

OK: All the packages are installed
Selecting previously deselected package nvidia-new-kernel-source.
(Reading database ... 130631 files and directories currently installed.)
Unpacking nvidia-new-kernel-source (from nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-new-kernel-source (100.14.11+2.6.20-16) ...
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/nv-kernel.o
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/nv-misc.h
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Done!

Updated infos about 85 packages
Extracting the package tarball, /usr/src/nvidia-new-kernel-source.tar.gz, please wait...
Done with /usr/src/nvidia-kernel-2.6.20-16-generic_100.14.11-0ubuntu3+2.6.20-16.29_i386.deb .
Selecting previously deselected package nvidia-kernel-2.6.20-16-generic.
(Reading database ... 130636 files and directories currently installed.)
Unpacking nvidia-kernel-2.6.20-16-generic (from .../nvidia-kernel-2.6.20-16-generic_100.14.11-0ubuntu3+2.6.20-16.29_i386.deb) ...
Setting up nvidia-kernel-2.6.20-16-generic (100.14.11-0ubuntu3+2.6.20-16.29) ...

Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 130643 files and directories currently installed.)
Unpacking nvidia-glx-new (from nvidia-glx-new_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-glx-new (100.14.11+2.6.20-16) ...

Selecting previously deselected package nvidia-glx-new-dev.
(Reading database ... 130692 files and directories currently installed.)
Unpacking nvidia-glx-new-dev (from nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-glx-new-dev (100.14.11+2.6.20-16) ...
Cleaning the build system:
NOTE: The following are only warnings
The build system is now clean
ENVY: Operation Completed
```

```
lvliv@lvliv-ubuntubox:~$ sudo aptitude search nvidia
Password:
c   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
i   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
i   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9631          -                                           
v   nvidia-kernel-1.0.9755          -                                           
v   nvidia-kernel-100.14.11         -                                           
i   nvidia-kernel-2.6.20-16-generic - NVIDIA binary kernel module for Linux 2.6.
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
i   nvidia-new-kernel-source        - NVIDIA binary 'new' kernel module source  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool           
lvliv@lvliv-ubuntubox:~$ 


```

There we go

---

### Post by tseliot on 2007-08-25
the installation went well...

can you post your xorg.conf ?

NOTE: please use CODE instead of QUOTE when you paste the content of your files otherwise we'll waste too much space

---

### Post by leveliv on 2007-08-25
oh lmao okay alright  ```
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
	Identifier	"nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by leveliv on 2007-08-25
"nv" to "nvidia" perhaps?

---

### Post by tseliot on 2007-08-25
> **leveliv said:**
> "nv" to "nvidia" perhaps?
yes, exactly

---

### Post by leveliv on 2007-08-25
I'll try it. thanks tseliot

---

### Post by leveliv on 2007-08-25
yeah that didn't work I had to reconfigure my xserver...cuz it crashed...any other ideas?

---

### Post by sonicborg on 2007-08-25
am in much the same problem, when i use nvidia driver, it just doesnt even load X, when i go back to nv its slugglish.
envy just doesnt work for me, so i use synaptic to isntall everything i can for nvidia, but i dont even get to select it in restricted drivers :(

my post = [http://ubuntuforums.org/showthread.php?t=534655](http://ubuntuforums.org/showthread.php?t=534655)

---

### Post by tseliot on 2007-08-25
> **leveliv said:**
> yeah that didn't work I had to reconfigure my xserver...cuz it crashed...any other ideas?
you should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

