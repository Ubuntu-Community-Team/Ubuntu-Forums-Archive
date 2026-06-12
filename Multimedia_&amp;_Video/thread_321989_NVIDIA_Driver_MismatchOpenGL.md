---
title: "NVIDIA Driver Mismatch/OpenGL"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by ikaritensi on 2006-12-19
Hello,
  I'm a real big n00b when it comes to Linux and Ubuntu and I'm have a big problem with my video card right now.  Currently I have a NVIDIA GeForce 4 MX 4000 vid card.  I'm attempting to get openGL support for it and thought I would attempt to install another driver besides the one provided by AUTOMATIX.  I went into Runlevel 1 after downloading the 9629 driver strait from NVIDIA and installed it in the terminal.  After I installed and attempted to reboot, my X Server wouldn't restart.  After two days of fiddling I discovered I could go into Recovery Mode and install the driver and then go into run level 5 and get into my computer (This was 2 mins before I was gonna scrap it and just fresh reinstall.)  But I have to do this every time I want to boot and I still don't get the OpenGL support from the card that I need.  I'll post my error messages and my log files below and if someone would help me out, I would be very greatful.

During Installation Errors:
NVIDIA-installer was unable to determine the correct X library installation path and will install the NVIDIA X libraries to '/usr/lib'.

You appear to be using a modular X.org release, but nvidia-installer was unable to determine the correct x module installation path with the 'pkg-config' utility.  Please install X.org SDK/Development package for your distribution (Tried this but couldn't find the files in symantiac.)

nvidia-installer was unable to determine the correct X module installation path and will install the NVIDIA X driver components to '/usr/lib/xorg/modules'.  If X fails to find the NVIDIA driver module, please correct and 'pkg-config' problems warned about earlier and reinstall the driver.


Log from startup:
Error:  API mismatch: the NVIDIA kernel module has the version 1.0-8776, but the x module has the version 1.0-9629.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

Log from computer:

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux hickit 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Tue Dec 19 19:55:58 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "COMPAQ 7500"
(**) |   |-->Device "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) PCI: 00:00:0: chip 8086,1130 card 107b,0111 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,1132 card 107b,0111 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 05 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 05 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0111 rev 05 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0111 rev 05 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0111 rev 05 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 107b,0111 rev 05 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 107b,0111 rev 05 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 8086,2449 card 8086,3013 rev 03 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 11c1,044c card 11c1,044c rev 02 class 07,80,00 hdr 00
(II) PCI: 01:0a:0: chip 10de,0185 card 1682,201f rev c1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4700000 - 0xf47fffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82815 CGC [Chipset Graphics Controller] rev 2, Mem @ 0xf8000000/26, 0xfeb80000/19
(--) PCI:*(1:10:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9e0000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[1] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[2] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[6] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[7] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[8] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[1] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[2] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[6] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[7] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[8] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[9] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
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
	[4] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[5] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[6] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[19] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[20] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
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
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
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
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:0a:0
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
	[4] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[5] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[6] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[19] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[20] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[5] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[6] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[22] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[23] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:1:10:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.36.04
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at
(--) NVIDIA(0):     PCI:1:10:0:
(--) NVIDIA(0):     COMPAQ 7500 (CRT-0)
(--) NVIDIA(0): COMPAQ 7500 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfe9dec00 - 0xfe9decff (0x100) MX[B]
	[7] -1	0	0xfe9df000 - 0xfe9dffff (0x1000) MX[B]
	[8] -1	0	0xe4700000 - 0xe471ffff (0x20000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[25] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
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
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-93.xkm


And to clarify about some other things with the Video on my computer.  I cannot install Ubuntu with my NVIDIA video card turned on so I turn it off and install the OS with my integrated Intel video card and then download Automatix and get the NVIDIA drivers and THEN turn the card on and plug my monitor into it.  Just wanted to clarify that so you don't look at the Log and say, "What the crap?"

Thanx for taking the time to read!
Until we meet again~
CG Nobles

PS:  Just thought I would throw this out there, I'm trying to run WOW on my computer and whenever I try to go into OpenGL mode with the game, it states that its unable to start 3D Acceleration for the game . . . any thoughts?

---

### Post by Beowulf.1000 on 2006-12-19
Well I am not much help if any here, just crying with you-- I need to get my nvidia GeForce 7900GT pci card working with Ubuntu i386 6.10.  I keep running into similar problems as you. And I have successfully installed the nvidia downloaded driver from nvidia.com and configured it before-- in Mandriva linux, But now I want to get it working with Ubuntu. FWIW, in Mandriva, I got it working nicely, including playing over a hundred hours of World of Warcraft with it using Cedega, superb performance and no problems-- so have faith, it can be done. (be sure to check cedega WoW wiki once you get openGL working, as you need to edit a couple of lines in a cedega file then Wow works great).

It would help if I/we could figure out where to get the kernel source for my 2.6.17-10-generic kernel, as I recall nvidia wanting that kernel source when I did this in Mandriva, for building the custom module for the nvidia driver.

Also, with Mandriva and nividia, I went through some hoops to manually copy paste some extra screen modes for the xorg.conf file once it was created in a basic form by the nvidia install, but that does not help me yet as I am getting similar errors as you mentioned-- nvidia *seems* to install, but with problems, and then the xorg.conf does not work.

We need to work through this here-- genius in numbers, lets share what works and what does not, I can check here daily.



> **ikaritensi said:**
> Hello,
  I'm a real big n00b when it comes to Linux and Ubuntu and I'm have a big problem with my video card right now.  Currently I have a NVIDIA GeForce 4 MX 4000 vid card.  I'm attempting to get openGL support for it and thought I would attempt to install .....

PS:  Just thought I would throw this out there, I'm trying to run WOW on my computer and whenever I try to go into OpenGL mode with the game, it states that its unable to start 3D Acceleration for the game . . . any thoughts?

---

### Post by hal10000 on 2006-12-20
The latest driver from the nvidia-site is 1.0-9631.

Download: in a terminal window type:
wget "http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run"

resp. if you have 64bit amd-system:
wget "http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9631/NVIDIA-Linux-x86_64-1.0-9631-pkg2.run"

Be sure you have installed at least the following packages:
gcc
bin86
linux-headers (according to your linux-image, supposedly linux-headers-2.6.17-10)
xorg-dev
xserver-xorg-dev

After downloading the driver, type:
[COLOR="Red"]sh NVIDIA-Linux-x86-1.0-9631-pkg1.run[/COLOR]
When the installer asks for creating a new /etc/X11/xorg.conf file, say yes (your old xorg.conf will be backuped).

You don't need kernel sources, just the kernel-headers.

Hope this helps, good luck.

---

### Post by Beowulf.1000 on 2006-12-20
I am a bit confused on which nvidia file to download. I have an AMD64 system, but I installed the Ubuntu i386 CD ("Alternate")..  So I am guessing I am running a 32 bit kernel, not the 64 bit kernel (especially since I had at first installed the AMD64 Ubuntu which then in Synaptic did not have Wine and a few other apps available; since reinstalling the i386 version of Ubuntu I was able to select Wine from Synaptic. So, should I install the AMD64 or the x86 version of the nvidia driver download from nvidia?

Also, I made a post on alt.os.linux related to this and got a useful reply-- some nice commands to first get rid of any nvidia related crap on my system that I might have installed using Synaptic prior to wanting to do the install manually they way we are trying to do here. Here are those commands. I also unchecked (removed) the Synaptic nvidia driver package.

POSTING OFF ALT.OS.LINUX :
[I][INDENT]
A clean install of Ubuntu puts a couple of entries in your grub boot
menu, choose the one labelled... err.... I think it was rescue mode or
something.  That puts you in run-level 1.  Don't bother changing to
run-level 3 or whatever the drivers ask for as every other run-level is
mapped to 5, starting the X-server and gnome.  I couldn't find a list of
services the nVidia driver install expects to be running, but for me at
least, the drivers installed without a hitch in run-level 1 without
starting any extra services.

I do recommend uninstalling anything you can find that has to do with
nVidia before you try the nVidia drivers:

sudo apt-get remove ^nvidia* nvtv ^nvclock*
^linux-restricted-modules-2.6* xserver-xorg-video-nv

Once the driver install is completed, check your /etc/X11/xorg.conf file
for the line
    Driver         "nvidia"

If that exists, you should be fine, if it says
    Driver         "nv"
then adjust it.

Finally if X won't boot, press ctrl-alt-F1 (or any key up to F6) to get
a useable console.  You can try uninstalling/reinstalling etc.  Then
once you're ready kill your X-server and gnome/kde and restart it, or
just restart your computer.[/INDENT][/I]





> **hal10000 said:**
> The latest driver from the nvidia-site is 1.0-9631.

Download: in a terminal window type:
wget "http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run"

resp. if you have 64bit amd-system:
wget "http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9631/NVIDIA-Linux-x86_64-1.0-9631-pkg2.run"

Be sure you have installed at least the following packages:
gcc
bin86
linux-headers (according to your linux-image, supposedly linux-headers-2.6.17-10)
xorg-dev
xserver-xorg-dev

After downloading the driver, type:
[COLOR="Red"]sh NVIDIA-Linux-x86-1.0-9631-pkg1.run[/COLOR]
When the installer asks for creating a new /etc/X11/xorg.conf file, say yes (your old xorg.conf will be backuped).

You don't need kernel sources, just the kernel-headers.

Hope this helps, good luck.

---

### Post by Beowulf.1000 on 2006-12-20
This info below might help us-- copied off Nvidia's website linux discussion forum:
[INDENT]
Debian GNU/Linux or Ubuntu with Xorg 7.x
If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:
    DISABLED_MODULES="nv"
If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)[/INDENT]


[QUOTE=Beowulf.1000;1908919]Well I am not much help if any here, just crying with you-- I need to get my nvidia GeForce 7900GT pci card working with Ubuntu i386 6.10....

---

### Post by Beowulf.1000 on 2006-12-20
Success! Ok I just had the worst night's sleep in years, total insomnia, so I got up and just tried this thing. I have nividia driver installed! Heck if I can do it on low sleep anybody can. Basically I had to get all the nvidia crap off my Ubuntu system that I had put there from what I thought was good advice from other websites, Synaptic, etc-- I removed the nvidia driver Synaptic had listed, did a bunch of commands as seen in posts on this thread to (1) remove all the nvidia crap that had been on my system (beware, you will no longer have X GUI until you then succeed installed the driver (2) add software as indicated in postings here, using apt-get, then (3) boot into rescue mode to get console with root # prompt, and run the nvidia install program that was downloaded. That was it. I now have about 17,000 fps from
  $ glxgears -printfps
which is much better than the crappy 700 fps I had been getting.

---

### Post by tseliot on 2006-12-20
You could have tried [Envy]("http://albertomilone.com/nvidia_scripts1.html") as well

---

### Post by Beowulf.1000 on 2006-12-20
Nice link/info, thank you. Yeah linux needs more automated scripts to handle things like nvidia cards, codecs for multimedia, etc.-- common hassels for setting up linux compared to MS-Windows.  I mean let's face it, with Windows you put in a CD that comes with the video card, click the setup.exe and presto magico you are good to go; I love linux, but it has to get easier for graphics card, although I understand part of it is the nature of the beast, and that vendors need to release their code for the FOSS community to write drivers, etc.

> **tseliot said:**
> You could have tried [Envy]("http://albertomilone.com/nvidia_scripts1.html") as well

---

### Post by ikaritensi on 2006-12-21
Now mine works great as well.  Thank you everyone.

---

