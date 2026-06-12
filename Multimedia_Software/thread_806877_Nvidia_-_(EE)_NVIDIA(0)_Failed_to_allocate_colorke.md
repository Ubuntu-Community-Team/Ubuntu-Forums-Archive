---
title: "Nvidia - (EE) NVIDIA(0): Failed to allocate colorkey"
date: 2008-05-25
forum: Multimedia Software
---

### Post by CrucialCa on 2008-05-25
Hi everybody - please assist if you can.  

I have an older machine with a Nvidia Ti4600 video card.  This card is supported by the nvidia legacy drivers, however I am unable to get X to work with the correct driver.  I have attempted to manually install the driver as well as use envy.  Both installations go well, but upon starting X with the "nvidia" driver, my monitor has some garbled images and apparently no response from keyboard or mouse.  The caps lock/num locks keys still respond and I can SSH to the box, so the machine isn't locked.

Also, upon changing the driver from "nvidia" to "nv", X properly starts up, but the window lag and refresh response is pretty poor. 

Here's the xorg.0.log:


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
Current Operating System: Linux 9BlueStem 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 25 10:25:17 2008
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
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 10b9,1647 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10b9,5247 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 10b9,5237 card 10b9,5237 rev 03 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10b9,5229 card 1043,8053 rev c4 class 01,01,ea hdr 00
(II) PCI: 00:05:0: chip 13f6,0111 card 1043,80e2 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10b9,5237 card 10b9,5237 rev 03 class 0c,03,10 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 10b9,1533 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:0a:0: chip 8086,1229 card 8086,0040 rev 0c class 02,00,00 hdr 00
(II) PCI: 00:0d:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 00:0d:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
(II) PCI: 00:11:0: chip 10b9,7101 card 0000,0000 rev 00 class 06,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0250 card 0000,0000 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe7700000 - 0xefffffff (0x8900000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:13:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe6800000/12
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4600] rev 163, Mem @ 0xe5000000/24, 0xe8000000/27, 0xe7800000/19, BIOS @ 0xe77e0000/17
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[1] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[2] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[3] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[4] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[7] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[11] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[12] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[1] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[2] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[3] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[4] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[7] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[11] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[12] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
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
	[4] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[5] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[6] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[7] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[8] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[11] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[5] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[6] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[7] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[8] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[11] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[5] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[6] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[7] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[8] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[11] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4600 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.27.10
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4600 at PCI:1:0:0:
(--) NVIDIA(0):     LG 15 TFTLCD MNT (CRT-1)
(--) NVIDIA(0): LG 15 TFTLCD MNT (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (83, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe7800000 - 0xe787ffff (0x80000) MX[B]
	[1] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[2] 0	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[8] -1	0	0xe2000000 - 0xe201ffff (0x20000) MX[B]
	[9] -1	0	0xe2800000 - 0xe2800fff (0x1000) MX[B]
	[10] -1	0	0xe3800000 - 0xe3800fff (0x1000) MX[B]
	[11] -1	0	0xe4800000 - 0xe4800fff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe77e0000 - 0xe77fffff (0x20000) MX[B](B)
	[14] -1	0	0xe7800000 - 0xe787ffff (0x80000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate colorkey
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) Loading extension NV-GLX

```

---

