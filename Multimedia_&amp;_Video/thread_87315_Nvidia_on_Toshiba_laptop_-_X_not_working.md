---
title: "Nvidia on Toshiba laptop - X not working"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by mauggie on 2005-11-07
Hi, an absolute beginner here.  Quite frustrated at this point.  I have a AMD64 PC and a Toshiba TE2100 laptop.  I decided to install ubuntu (breezy) on both.  I have manually installed the NVidia driver on both.  The AMD is no problem, the Toshiba just will not work.  I have tried so many things that I am confused about what state the system is in at this stage.  I really do think that the driver is OK and it is a problem with the xorg.conf file, but I have absolutely no linux experience and the amount of info is so far more overwhelming than informative.  It works straight after the install (I am using the laptop here) but only with 640x480, maybe there is an easier way of getting better resolution than installing the Nvidia driver?  Any help appreciated..  Oh my Xorg.0.log file contents are as follows:


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  8 12:37:08 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 420 Go]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2487 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 1179,0001 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 1179,0001 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0175 card 1179,0001 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1031 card 1179,0001 rev 42 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1179,0617 card 4000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card 4800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 03:00:0: chip 168c,0013 card 1186,3a12 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdbf00000 - 0xdfffffff (0x4100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:11:0), (2,3,6), BCTRL: 0x0500 (VGA_EN is cleared)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (2:11:1), (2,7,10), BCTRL: 0x0580 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 420 Go] rev 163, Mem @ 0xfd000000/24, 0xdc000000/26, 0xdbf80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x20800000 - 0x2080ffff (0x10000) MX[B]
	[1] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[2] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[6] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[8] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[9] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[10] -1	0	0x00001040 - 0x0000107f (0x40) IX[B]
	[11] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[12] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[13] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[14] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[15] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[16] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[17] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[18] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[19] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x20800000 - 0x2080ffff (0x10000) MX[B]
	[1] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[2] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[5] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[6] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[8] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[9] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[10] -1	0	0x00001040 - 0x0000107f (0x40) IX[B]
	[11] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[12] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[13] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[14] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[15] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[16] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[17] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[18] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[19] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x20800000 - 0x2080ffff (0x10000) MX[B]
	[6] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[7] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[15] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[16] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[17] -1	0	0x00001040 - 0x0000107f (0x40) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[20] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[21] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[22] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[23] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[24] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA X Driver  1.0-7676  Fri Jul 29 13:01:02 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x20800000 - 0x2080ffff (0x10000) MX[B]
	[6] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[7] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[15] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[16] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[17] -1	0	0x00001040 - 0x0000107f (0x40) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[20] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[21] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[22] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[23] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[24] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x20800000 - 0x2080ffff (0x10000) MX[B]
	[6] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[7] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[18] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[19] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[20] -1	0	0x00001040 - 0x0000107f (0x40) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[23] -1	0	0x0000cfe4 - 0x0000cfe4 (0x1) IX[B]
	[24] -1	0	0x0000cfe8 - 0x0000cfe8 (0x1) IX[B]
	[25] -1	0	0x0000cff4 - 0x0000cff4 (0x1) IX[B]
	[26] -1	0	0x0000cff8 - 0x0000cff8 (0x1) IX[B]
	[27] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[28] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[29] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "IgnoreEDID" "1"
(**) NVIDIA(0): Option "NoDDC" "1"
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(**) NVIDIA(0): Ignoring EDIDs
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by 23meg on 2005-11-07
It seems the Nvidia kernel module hasn't been compiled. Did you follow the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074") to install the official Nvidia driver? If not, give it a try.

---

### Post by mauggie on 2005-11-07
[QUOTE=23meg]It seems the Nvidia kernel module hasn't been compiled. Did you follow the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074") to install the official Nvidia driver? If not, give it a try.[/QUOTE]
Yep I did.  I used Method 3 and as far as I knew it worked fine.  I will do it again using method 1 and see how I go.  Thanks.

---

