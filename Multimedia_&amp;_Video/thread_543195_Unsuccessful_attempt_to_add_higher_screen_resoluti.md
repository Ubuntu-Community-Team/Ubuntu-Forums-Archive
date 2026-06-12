---
title: "Unsuccessful attempt to add higher screen resolutions"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by impeachme2 on 2007-09-04
[COLOR="Gray"]I know there's a lot of posts for adding screen resolutions to for Nvidia cards.  I cannot get the posted solutions to work.  Keep in mind I am new to Linux.

OS:Feisty
Card:GeForce 3
Monitor Type:CRT
Nvidia driver successfully installed via "Envy"


Attempt to edit xorg.conf failed.
Attempt to reconfigure xserver-xorg failed.


I am not receiving additional resolutions after restarting in either:
     System:Prefs:Screen Resolution
     Applications:System Tools: Nvidia Settings[/COLOR]

---

### Post by impeachme2 on 2007-09-05
I found out why I was unable to add resolutions: I had the incorrect driver installed, which was ignoring my GPU.  I need to use a Legacy driver for my GeForce 3. 

I have installed the Legacy driver, but I cannot load X server after restarting.  I receive an error when it attempts to load the log-in screen, informing me that there is something wrong with my xorg.conf.  I'm assuming it didn't create a new xorg.conf during installation that is compatible with the driver.

Nvidia includes a sample xorg.conf, which I would like to try.  I am not familiar with editing text files in a non-gui terminal.  Currently I am running straight off the Ubuntu cd.  Is there any way to edit my xorg.conf while running off the Ubuntu boot disk, or will I need to edit xorg.conf in the terminal.  If the later is the case, how do I go about doing that?


This is the log file recorded while attempting to start X server:

```
[SIZE="1"]X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux danny-ubuntu 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  5 00:14:29 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "GeForce 3"
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 103c,2a04 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 103c,2a04 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 103c,2a05 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 103c,2a04 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 103c,2a04 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 103c,2a04 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 103c,2a04 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 103c,2a04 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 103c,2a04 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 1106,3044 card 0003,000f rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0200 card 1554,10d1 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xdbffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xe3ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3] rev 163, Mem @ 0xd4000000/24, 0xdc000000/26, 0xe0000000/19
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd0000000 to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe5005000 - 0xe50057ff (0x800) MX[B]
	[1] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[2] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[3] -1	0	0xe5001000 - 0xe5001fff (0x1000) MX[B]
	[4] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[5] -1	0	0xe5004000 - 0xe5004fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[20] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5005000 - 0xe50057ff (0x800) MX[B]
	[1] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[2] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[3] -1	0	0xe5001000 - 0xe5001fff (0x1000) MX[B]
	[4] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[5] -1	0	0xe5004000 - 0xe5004fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[20] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
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
	[4] -1	0	0xe5005000 - 0xe50057ff (0x800) MX[B]
	[5] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[6] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[7] -1	0	0xe5001000 - 0xe5001fff (0x1000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5004000 - 0xe5004fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[13] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
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
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
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
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-7185  Mon Apr  2 13:04:18 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5005000 - 0xe50057ff (0x800) MX[B]
	[5] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[6] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[7] -1	0	0xe5001000 - 0xe5001fff (0x1000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5004000 - 0xe5004fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[13] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[26] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5005000 - 0xe50057ff (0x800) MX[B]
	[5] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[6] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[7] -1	0	0xe5001000 - 0xe5001fff (0x1000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5004000 - 0xe5004fff (0x1000) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[12] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[13] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[29] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/SIZE]
```

---

### Post by impeachme2 on 2007-09-05
This is the sample xorg.conf file included with the Nvidia Legacy Driver Installation.  If possible, can anyone piece together the xorg.conf I should have in place, using this sample xorg.conf?

```
[SIZE="1"]##########################################################################
# Sample XF86Config file for NVIDIA XFree86 drivers.
#
# Refer to the XF86Config(4/5) man page for details about the format of
# this file.
#
# Be sure to replace the monitor values with correct values for your
# monitor!
##########################################################################


Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"
    FontPath   "unix/:-1"

EndSection


##########################################################################
# Server flags section.
##########################################################################

Section "ServerFlags"

    # Uncomment this to cause a core dump at the spot where a signal is
    # received.  This may leave the console in an unusable state, but may
    # provide a better stack trace in the core dump to aid in debugging
    #NoTrapSignals

    # Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
    # This allows clients to receive this key event.
    #DontZap

    # Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
    # sequences.  This allows clients to receive these key events.
    #DontZoom

    # This  allows  the  server  to start up even if the
    # mouse device can't be opened/initialised.
    AllowMouseOpenFail

EndSection


##########################################################################
# Input devices
##########################################################################

#
# Keyboard section
#
Section "InputDevice"

    Identifier "Keyboard1"
    Driver     "Keyboard"
    Option     "AutoRepeat"  "250 30"

    Option "XkbRules"  "xfree86"
    Option "XkbModel"  "pc105"
    Option "XkbLayout" "us"

EndSection


#
# Pointer section
#
Section "InputDevice"

    Identifier  "Mouse1"
    Driver      "mouse"
    Option      "Protocol"    "IMPS/2"
    Option      "Device"      "/dev/psaux"

EndSection


##########################################################################
# Module section
##########################################################################

Section "Module"

    Load        "dbe"

    # Load the glx module.
    Load	"glx"

    Load        "extmod"

    Load	"type1"
    Load	"freetype"
EndSection


##########################################################################
# Monitor section
##########################################################################

Section "Monitor"

    Identifier "MyMonitor"
    VendorName "Mitsubisi"
    ModelName  "Diamond Plus 120u"

    # be sure to replace these values with values appropriate for your
    # monitor!
    HorizSync  31-82
    VertRefresh 55-120

    # 3840x2400 @ 12Hz for IBM's T221 FlatPanel
    Modeline "3840x2400" 148.0 3840 3944 4328 4816 2400 2401 2404 2418 

EndSection


##########################################################################
# Graphics device section(s)
##########################################################################

Section "Device"
    Identifier  "NV AGP"
    VendorName  "nvidia"
    Driver   "nvidia"
    # update this with the PCI id of your card.  Consult the output
    # of the 'lspci' command.  The BusID is usually optional when
    # only using one graphics card.
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier "NV PCI"
    VendorName "nvidia"
    Driver "nvidia"
    # update this with the PCI id of your card.  Consult the output
    # of the 'lspci' command.  The BusID is usually optional when
    # only using one graphics card.
    BusID       "PCI:0:13:0"
EndSection

Section "Device"
    Identifier "NV AGP TwinView"
    VendorName "nvidia"
    Driver "nvidia"
    # update this with the PCI id of your card.  Consult the output
    # of the 'lspci' command. The  BusID is usually optional when
    # only using one graphics card.
    BusID       "PCI:1:0:0"

    # sample twinview setup
    Option "TwinView"
    # be sure to replace the HorizSync and VertRefresh with correct values
    # for your monitor!  
    Option "SecondMonitorHorizSync"   "31-82"
    Option "SecondMonitorVertRefresh" "55-120"
    Option "TwinViewOrientation"      "RightOf"
    Option "MetaModes"                "1280x1024,1280x1024; 1024x768,1024x768"
    Option "ConnectedMonitor"         "crt,crt"
EndSection


##########################################################################
# Screen sections
##########################################################################

#
# screen section for an nvidia AGP card
#
Section "Screen"
    Identifier "Screen AGP"
    Device      "NV AGP"
    Monitor     "MyMonitor"
    DefaultColorDepth 24
    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x400"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection

EndSection


#
# screen section for an nvidia PCI card
#
Section "Screen"
    Identifier "Screen PCI"
    Device      "NV PCI"
    Monitor     "MyMonitor"
    DefaultColorDepth 24
    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x400"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

#
# screen section for an nvidia AGP TwinView card
# (look at the appropriate Device section)
#
Section "Screen"
    Identifier "Screen AGP TwinView"
    Device "NV AGP TwinView"
    Monitor "MyMonitor"
    DefaultColorDepth 24
    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x400"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection


##########################################################################
# ServerLayout sections
# (invoke using the '-layout' option of 'startx'.
##########################################################################

#
# just one agp card
#
Section "ServerLayout"
    Identifier  "AGP"
    Screen      "Screen AGP"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

#
# just one pci card
#
Section "ServerLayout"
    Identifier  "PCI"
    Screen      "Screen PCI"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

#
# 2 cards, non twinview
#
Section "ServerLayout"
    Identifier  "Both"
    Screen      "Screen AGP"
    Screen      "Screen PCI" LeftOf "Screen AGP"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

#
# just one agp twinview card
#
Section "ServerLayout"
    Identifier  "AGPTwinView"
    Screen      "Screen AGP TwinView"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

#
# 2 cards, one agp twinview and one pci (3 monitors total)
#
Section "ServerLayout"
    Identifier  "BothTwinView"
    Screen      "Screen AGP TwinView"
    Screen      "Screen PCI" LeftOf "Screen AGP TwinView"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection[/SIZE]
```

---

### Post by Sp4freel on 2007-09-07
well to edit your Xorg.conf file in the term.
Sudo gedit /etc/x11/xorg.conf 

that will let you into the file so that you can edit it

---

