---
title: "nvidia legacy and screen resolution"
date: 2008-05-01
forum: Multimedia Software
---

### Post by bobismeyep on 2008-05-01
ok... i know that this has been posted MANY MANY times but i can never find a solution to my problem.

I am using an older computer which means an older NVIDIA TNT 2.  I know that this graphics card needs the nvidia-glx-legacy driver for it to run the 3D, and desktop fx, and so on...  Well when i have the driver turned off (System > Admin > Hardware Drivers) the screen resolution is perfect for my display.  However when i have it on I am limited to 800 x 600 as my resolution.  After looking though countless threads and websites for countless hours i have yet to find a solution that fits me, so i was wondering if someone could take me step by step to help me fix this problem.

I thank you in advance for your help!

P.S. I'm pretty sure you're going to ask me for my /etc/X11/xorg.conf at some point.  But until someone asks me to I'll wait.

---

### Post by Zorael on 2008-05-02
Please provide your /etc/X11/xorg.conf! :>

Also, your /var/log/Xorg.0.log.

---

### Post by bobismeyep on 2008-05-02
Here's my current xorg.conf. As you can see it's basically nothing at the moment, except for the display size (i did that to change DPI).

```

...

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nv"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Displaysize    359    203
EndSection

Section "Extensions"
EndSection

```

Here's my log (it's REALLY long):

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
Current Operating System: Linux bryansold 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May  2 15:14:30 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
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
	Using the first core pointer device.
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
(II) PCI: 00:00:0: chip 0003,0600 card 1043,8025 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 12 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 12 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 104d,80f0 rev 12 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 104d,80f0 rev 12 class 0c,03,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 104d,80f0 rev 12 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 104d,80e4 rev 12 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002d card 1043,4003 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11c1,044e card 13e0,0401 rev 02 class 07,80,00 hdr 00
(II) PCI: 02:0d:0: chip 10ec,8139 card 104d,80ea rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0e:0: chip 104c,8020 card 104d,80d2 rev 00 class 0c,00,10 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5efffff (0x1f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf5f00000 - 0xf7ffffff (0x2100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[4] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[5] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xf4000000/24, 0xf6000000/25, BIOS @ 0xf5ff0000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[1] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[2] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[3] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[6] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[11] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[1] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[2] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[3] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[6] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[11] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
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
	[4] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[6] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[7] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[10] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.1.8
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
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT,
	GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M,
	Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT,
	GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS,
	GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M,
	Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290,
	GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT,
	Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset RIVA TNT2 Model 64 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[6] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[7] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[10] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[6] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[7] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[10] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2 Model 64"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF6000000
(--) NV(0): MMIO registers at 0xF4000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: SYN  Model: 31  Serial#: 354
(II) NV(0): Year: 2007  Week: 38
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 82  vert.: 46
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.641 redY: 0.336   greenX: 0.277 greenY: 0.608
(II) NV(0): blueX: 0.141 blueY: 0.073   whiteX: 0.284 whiteY: 0.292
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 109.0 MHz   Image Size:  820 x 460 mm
(II) NV(0): h_active: 1360  h_sync: 1408  h_sync_end 1552 h_blank_end 1804 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 800 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 79.5 MHz   Image Size:  820 x 460 mm
(II) NV(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 72.0 MHz   Image Size:  820 x 460 mm
(II) NV(0): h_active: 1360  h_sync: 1408  h_sync_end 1440 h_blank_end 1520 h_border: 0
(II) NV(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) NV(0): Monitor name: 537-B12
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004f2e310062010000
(II) NV(0): 	261101030e522e782b033fa456479b24
(II) NV(0): 	12484a254a0081c00101010101010101
(II) NV(0): 	010101010101942a50bc510020303090
(II) NV(0): 	330034cc3100001c0e1f008051001e30
(II) NV(0): 	4080370034cc3100001a201c50a05000
(II) NV(0): 	16303020250034cc3100001c000000fc
(II) NV(0): 	003533372d4231320a20202020200011
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "SYN", prod id 49
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1360x768"x0.0  109.00  1360 1408 1552 1804  768 771 774 800 -hsync +vsync (60.4 kHz)
(II) NV(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
(II) NV(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 770 775 790 -hsync +vsync (47.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 31.50-60.42 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 59.86-75.53 Hz
(II) NV(0): Estimated virtual size for aspect ratio 1.7685 is 1360x768
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (height too large for virtual size)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (height too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NV(0): Not using default mode "576x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1152x864" (height too large for virtual size)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 1360x768 (pitch 1360)
(**) NV(0): *Driver mode "1360x768": 109.0 MHz, 60.4 kHz, 75.5 Hz
(II) NV(0): Modeline "1360x768"x75.5  109.00  1360 1408 1552 1804  768 771 774 800 -hsync +vsync (60.4 kHz)
(**) NV(0): *Driver mode "1360x768": 72.0 MHz, 47.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 770 775 790 -hsync +vsync (47.4 kHz)
(**) NV(0): *Driver mode "1280x768": 79.5 MHz, 47.8 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
(**) NV(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) NV(0): *Driver mode "1280x720": 74.5 MHz, 44.8 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"x60.2   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync (56.9 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"x60.0   41.73  640 672 740 840  400 400 402 414 doublescan (49.7 kHz)
(**) NV(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"x60.1   40.07  640 672 740 840  384 384 386 397 doublescan (47.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): Display dimensions: (359, 203) mm
(WW) NV(0): Probed monitor is 820x460 mm, using Displaysize 359x203 mm
(**) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B]
	[1] 0	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf2000000 - 0xf2003fff (0x4000) MX[B]
	[7] -1	0	0xf2800000 - 0xf28007ff (0x800) MX[B]
	[8] -1	0	0xf3000000 - 0xf30000ff (0x100) MX[B]
	[9] -1	0	0xf3800000 - 0xf38000ff (0x100) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf5ff0000 - 0xf5ffffff (0x10000) MX[B](B)
	[12] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[22] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xf6000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		30 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
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
SetClientVersion: 0 9
(II) 3rd Button detected: disabling emulate3Button
```

As you eventually read it does recognize that it is a NVIDIA TNT2 Model 64.  And as you see it's currently using the "nv" driver which the log obviously says supports a TON of nvidia cards (but again, not with glx).

Thank you for your help!

---

### Post by MatthewAPeters on 2008-05-03
Cross post: [HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron]("http://ubuntuforums.org/showthread.php?t=780777")

This might help - not sure if your card qualifies as "legacy" or "new legacy".  Includes a copy of my xorg.conf - might have some clues.

Good luck!

---

### Post by bobismeyep on 2008-05-07
> **MatthewAPeters said:**
> Cross post: [HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron]("http://ubuntuforums.org/showthread.php?t=780777")

This might help - not sure if your card qualifies as "legacy" or "new legacy".  Includes a copy of my xorg.conf - might have some clues.

Good luck!

I tried to see if i could get any of the things to work but unfortunately i still have a problem.  Thanks anyway!

---

