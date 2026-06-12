---
title: "Nvidia problem even with envy"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by jon_z on 2006-09-29
cant get the nvidia drivers to work for gdm..  log is attached.```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux Whitebox 2.6.15-25-k7 #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 29 14:48:22 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 MX 440]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0305 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0686 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 30 class 0c,05,00 hdr 00
(II) PCI: 00:09:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 1102,0002 card 1102,8071 rev 07 class 04,01,00 hdr 80
(II) PCI: 00:0a:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 00:0e:0: chip 1274,1371 card 1458,2060 rev 07 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0171 card 10b0,0002 rev a3 class 03,00,00 hdr 00
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
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdde00000 - 0xdfefffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcdb00000 - 0xddcfffff (0x10200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 MX 440] rev 163, Mem @ 0xde000000/24, 0xd0000000/27, 0xddc80000/19, BIOS @ 0xdfee0000/17
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[3] -1	0	0xddc80000 - 0xddcfffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[7] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[1] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[2] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[3] -1	0	0xddc80000 - 0xddcfffff (0x80000) MX[B](B)
	[4] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[7] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[7] -1	0	0xddc80000 - 0xddcfffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[7] -1	0	0xddc80000 - 0xddcfffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[17] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffffc00 - 0xdfffffff (0x400) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[7] -1	0	0xddc80000 - 0xddcfffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by tseliot on 2006-09-29
can you post the output of this command?

```
lspci -n | grep 300
```

---

### Post by jon_z on 2006-09-29
01:00.0 0300: 10de:0171 (rev a3)

---

### Post by jon_z on 2006-09-30
bump

---

### Post by tseliot on 2006-09-30
> **jon_z said:**
> 01:00.0 0300: 10de:0171 (rev a3)

Try point 7 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by jon_z on 2006-10-01
still a no go, here is what the error is when gdm goes to start:

```
FATAL: Could no open '/lib/modules/2.6.17-10-386/volatile/nvidia.ko' : No such file or directory
```

---

### Post by tseliot on 2006-10-01
Can I see your nvidia log which you can find in /var/log/

---

### Post by jon_z on 2006-10-01
the installer log from envy?

---

### Post by jon_z on 2006-10-01
I believe i am just going to do a fresh install, backing up my 120 gigs worth of files and making a seperate partition incase this happens again :-)

---

### Post by tseliot on 2006-10-01
> **jon_z said:**
> the installer log from envy?

no, the log of the Nvidia installer (which envy uses).

It's something like /var/log/nvidia-installer.log

---

### Post by jon_z on 2006-10-01
I think one of the problems may be in the fact that I have been getting a new kernel every time i re-boot and i cant see my grub when my comptuer boots up, it needs a clean install anyways.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Oct  1 13:34:32 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  force tls               : (not specified)
  X install prefix        : /usr/lib/xorg/modules
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.17-10-386
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.17-10-386' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.17-10-386'
-> Kernel output path: '/usr/src/linux-headers-2.6.17-10-386'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.1
   7-10-386 SYSOUT=/usr/src/linux-headers-2.6.17-10-386'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.17-10-386 SUBDIRS
   =/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv modules
   mkdir -p /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.tmp_vers
   ions
   rm -f /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.tmp_version
   s/*
   make -f scripts/Makefile.build obj=/usr/share/envy/NVIDIA-Linux-x86-1.0-8774
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /usr/share/envy/NVI
   DIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL_
   _ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O
   2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpre
   ferred-stack-boundary=2  -march=i486 -mtune=generic -mregparm=3 -ffreestandi
   ng -Iinclude/a
   sm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/usr/
   share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -
   Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -W
   no-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -DNVRM -DDYNAMI
   C_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8774  -UDEB
   UG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PR
   ESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_M
   ESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -
   DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESEN
   T  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)" -c -o /usr/share/envy/NVIDIA-Linux-x86-1.0-87
   74-pkg1/usr/src/nv/.tmp_nv.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/
   usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERN
   EL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector
   -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mp
   referred-stack-boundary=2  -march=i486 -mtune=generic -mregparm=3 -ffreestan
   ding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-poin
   ter-sign -I/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -
   Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM
   -DNVRM -DDYNAMIC_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLE
   VEL=8774  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BR
   IDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PR
   ESENT -DNV_PM_MESSAGE_T_PRESENT -DN
   V_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_
   PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUIL
   D_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)" -c -o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/n
   v/.tmp_nv-vm.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nv-
   vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protecto
   r -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -
   mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mregparm=3 -ffreest
   anding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-po
   inter-sign -I/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv -Wall
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpoin
   ter-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-
   cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -DN
   VRM -DDYNAMIC_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL
   =8774  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDG
   E_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESE
   NT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PA
   GE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_V
   MAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /usr/share/envy/NVIDIA-
   Linux-x86-1.0-8774-pkg1/usr/src/nv/.tmp_os-agp.o /usr/share/envy/NVIDIA-Linu
   x-x86-1.0-8774-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-ali
   asing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchrono
   us-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i48
   6 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default 
   -Wdeclaration-after-statement -Wno-pointer-sign -I/usr/share/envy/NVIDIA-Lin
   ux-x86-1.0-8774-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfo
   rmat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werro
   r -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KER
   NEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -DNVRM -DDYNAMIC_SLI  -DNV_MAJOR_VER
   SION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8774  -UDEBUG -U_DEBUG -DNDEBUG 
   -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CL
   ***_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV
   _PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_P
   RESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /usr/share
   /envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.tmp_os-interface.o /usr/sha
   re/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.os-r
   egistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-pro
   tector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-fl
   oat -mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mregparm=3 -ff
   reestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -W
   no-pointer-sign -I/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE 
   -DNTRM 
   -DNVRM -DDYNAMIC_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLE
   VEL=8774  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BR
   IDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PR
   ESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT
   _PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DN
   V_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_ST
   R(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /usr/share/envy
   /NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.tmp_os-registry.o /usr/share/env
   y/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.nv-i
   2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protecto
   r -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -
   mpreferred-stack-
   boundary=2  -march=i486 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/
   asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/usr
   /share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  
   -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -DNVRM -DDYNAM
   IC_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8774  -UDE
   BUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_P
   RESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_
   MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT 
   -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /usr/share/envy/NVIDIA-Linux-x86-1
   .0-8774-pkg1/usr/src/nv/.tmp_nv-i2c.
   o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:51,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-linux.h:76,
                    from /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src
   /nv/nv-i2c.c:8:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386  -r -o /usr/share/envy/NVIDIA-Linux-x86-1.0-877
   4-pkg1/usr/src/nv/nvidia.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/us
   r/src/nv/nv-kernel.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/
   nv/nv.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nv-vm.o /u
   sr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/os-agp.o /usr/share/
   envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/os-interface.o /usr/share/env
   y/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/os-registry.o /usr/share/envy/NV
   IDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nv-i2c.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.17-10-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-386/Module.s
   ymvers -I /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/Modules.
   symvers -o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/Modules
   .symvers /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nvidia.o
   WARNING: could not find /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/.nvid
   ia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D_
   _KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-prot
   ector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-flo
   at -mpreferred-stack-boundary=2  -march=i486 -mtune=generic -mregparm=3 -ffr
   eestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wn
   o-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /usr/share/envy/NVID
   IA-Linux-x86-1.0-8774-pkg1/usr/src/nv/nvidia.mod.o /usr/share/envy/NVIDIA-Li
   nux-x86-1.0-8774-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774
   -pkg1/usr/src/nv/nvidia.ko /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/us
   r/src/nv/nvidia.o /usr/share/envy/NVIDIA-Linux-x86-1.0-8774-pkg1/usr/src/nv/
   nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [  128.554852] IPv6 over IPv4 tunneling driver
   [  130.415501] powernow: No powernow capabilities detected
   [  130.455101] acpi_cpufreq: Unknown symbol cpu_online_map
   [  138.733512] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [  139.182149] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
   [  139.187994] eth0: no IPv6 routers present
   [  139.383802] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state
   recovery directory
   [  139.396234] NFSD: starting 90-second grace period
   [  141.641573] Bluetooth: Core ver 2.8
   [  141.641584] NET: Registered protocol family 31
   [  141.641588] Bluetooth: HCI device and connection manager initialized
   [  141.641616] Bluetooth: HCI socket layer initialized
   [  141.685396] Bluetooth: L2CAP ver 2.8
   [  141.685406] Bluetooth: L2CAP socket layer initialized
   [  141.691298] Bluetooth: RFCOMM socket layer initialized
   [  141.691331] Bluetooth: RFCOMM TTY layer initialized
   [  141.691335] Bluetooth: RFCOMM ver 1.7
   [  746.482057] powernow: No powernow capabilities detected
   [  746.527909] acpi_cpufreq: Unknown symbol cpu_online_map
   [ 1434.967276] nvidia: module license 'NVIDIA' taints kernel.
   [ 1434.986804] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8774  Tue
   Aug  1 20:54:08 PDT 2006
   [ 1461.203706] nvidia: `o' invalid for parameter `NVreg_SoftEDIDs'
   [ 1465.477805] nvidia: `o' invalid for parameter `NVreg_SoftEDIDs'
   [ 1469.810240] nvidia: `o' invalid for parameter `NVreg_SoftEDIDs'
   [ 1665.066872] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8774  Tue
   Aug  1 20:54:08 PDT 2006
-> Installing both new and classic TLS OpenGL libraries.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-8774):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: N
   o)
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-8774) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.

```

---

### Post by tseliot on 2006-10-02
> **jon_z said:**
> I think one of the problems may be in the fact that I have been getting a new kernel every time i re-boot and i cant see my grub when my comptuer boots up, it needs a clean install anyways.

nvidia-installer log file '/var/log/nvidia-installer.log'

You will need to recompile the driver (i.e. use envy) every time you change your kernel.

Anyway I can't see anything wrong in that log

---

