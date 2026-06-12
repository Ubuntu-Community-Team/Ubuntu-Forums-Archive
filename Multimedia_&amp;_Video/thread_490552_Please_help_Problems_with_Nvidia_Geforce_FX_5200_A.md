---
title: "Please help: Problems with Nvidia Geforce FX 5200 AGP 8x"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by DeleiMaciel on 2007-07-02
Hi all...
Please help me someone! I've could't find help... Months with the same trouble!!

I'm with some troubles with my nvidia card. And looking for some solution on the brazilian Ubuntu Feisty forum, I met some other guys (from Brazil and Uruguay, and other countries) who have the same problem with the same graphic card. 
My nvidia card is a "Nvidia GeForce FX 5200 - 128 MB - AGP 8X"   and I'm using the Ubuntu 7.04 with the newest update.

My problem is: when I start, the Ubuntu load perfectly, but when I'm wainting for the gdm screen, I hear the drums but the screen just don't appear! When I tried something like "Crtl + Alt + F1" and back to X with "ctrl + alt + F7" the gdm screen is there!! If I don't do this, but change the resolution with "crtl + alt + Nun + or -" the gdm appears too. If I login and try something who use the 3D acceleration, the pc just freeze!!! And I go to the "reset" button... :(

My first solution:
I've uninsttaled all nvidia drivers and install it again with 'aptitude'... So... my driver is nvidia-glx-new (that 1.0.9755) ... and I read a lot of Readme files and other documention in a lot of places... and find something saying to "disable the DRI module" 'cause this module "don't work in some graphic cards". Then I did it. With dpkg-reconfigure xserver-xorg, I disabled the DRI module. When I restart my computer, the gdm´s screen appears in the same time as i listen the drums the drums, and the 3D acceleration was working fine!! XD

And now:
A week ago I updated the sistem (and I'm sorry for that...) and I went back to the original problem... The 'nvidia-glx-new' package has been updated too, I guess...
I try uninstall and reinstall the drivers... but it just don't work anymore.

Friends, I'm a Biologist... I know more about frogs than about computers! :D
I'm just a single user!! I even know what is that DRI thing or if my AGP 8X works properly on my machine... :/

I've spent some nights on this... And a any help will be really really welcome... and it will help a lot of people, as I say...
If any other information would be necessary, please ask me.

Thanks for the chance!
And forgive me for my english...

---

### Post by DeleiMaciel on 2007-07-02
I almost forgot..
Here is the contents of /var/log/Xorg.0.log:
```
 X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux blackboy 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  2 13:00:56 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor Genérico"
(**) |   |-->Device "NVidia GeForce FX 5200"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
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
(II) PCI: 01:00:0: chip 10de,0322 card 1682,1351 rev a1 class 03,00,00 hdr 00
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
	[0] -1	0	0xfaf00000 - 0xfbffffff (0x1100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf9ffffff (0xa000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfb000000/24, 0xf0000000/27, BIOS @ 0xfaf00000/17
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
(II) PCI Memory resource overlap reduced 0xec000000 from 0xefffffff to 0xebffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[1] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[2] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[3] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[4] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[8] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[13] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[1] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[2] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[3] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[4] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[8] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[10] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[13] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
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
	[4] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[5] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[6] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
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
	[4] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[5] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[6] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[15] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[5] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[6] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[7] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.67.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     OEC (CRT-0)
(--) NVIDIA(0): OEC (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (92, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfac00000 - 0xfac000ff (0x100) MX[B]
	[7] -1	0	0xfad00000 - 0xfad000ff (0x100) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xfaf00000 - 0xfaf1ffff (0x20000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Setting mode "1024x768"
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
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
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/psaux"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/psaux"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

There's a lot of things with some error...
But I don't know how fix it....
...
Any help??
...
Tanks.

---

### Post by Jovec on 2007-07-02
My first instinct would be to try using the nvidia-glx-legacy package for your Nvidia drivers.  The 5200 I believe can use either the legacy drivers or either of the newer packages (nvidia-glx or nvidia-glx-new).

---

### Post by DeleiMaciel on 2007-07-02
I've try it! But don't work anyway...
When it was working, some days ago, only the nvidia-glx-new works properly.
Now, even it...
I'm downloading a driver from nvidia site.... I will try anything...
...
Tanks!

---

### Post by paulb75 on 2008-01-09
I have a similar problem with the same card-- a GeForce FX 5200 Ultra. I'm still trying to get it to work, and I've noticed something quite odd: it registers under the device manager as a PCI card when it's actually AGP (8x). Maybe this is nothing, but I'm looking for a patch to set things right. meanwhile, I'm using the default graphics which are still pretty good. I will probably need the card working though for molecular modelling.

I'm running Gutsy Gibbon 
Things I've tried (and failed):
1. Restricted Drivers Manager
2. X.Org "new driver"
3. downloading the drivers from NVIDIA and reinstalling
4. Envy

---

### Post by paulb75 on 2008-01-11
Umm, ok, I finally got it to work. :D

First off, if you've got a spare drive, then it might be better to do a clean install. I did because my attempts to fix this problem resulted in a lot of junk cluttering the HD. The steps I took (and worked too!) are as follows:

1. Installed the Restricted Drivers Manager. (Using the "Add/Remove Applications" menu)
2. Using the "Add/Remove Applications" menu, I installed the Package "NVidia binary X.Org driver ('new driver)"
3. Enabled "Restricted Drivers Manager: NVIDIA accelerated graphics driver (latest cards)
4. open Terminal: type "sudo enable nvidia-glx-config enable" (This is me being very very anal about it actually enabling the drivers--I think the RDM takes care of this step though, but I wanted to be sure). This gave me an error message, so I typed "md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum" 
5. in the Terminal: "sudo pico /etc/X11/xorg.config" (Yeah sorry, I'm still addicted to pico). Under "Device" check to make sure that "nv" is now "nvidia". Now, if you want a quick confirmation that all is well when things boot up, the line that says (Option "NoLogo"  "False") change "False" to "True". You can set it back to false later.
6. Reboot.

Apparently, the trick is AFTER installing the drivers, you have to type "sudo enable nvidia-glx-config enable". When I tried to set up the card without this, the drivres didn't work and I had to rollback to "nv". 

This has been quite a challenge. :) A bit frustrating, but soooo rewarding when you see all the iCandy running later. ;-)

Hope this helps!

---

### Post by BLTicklemonster on 2008-01-12
I run the same card, and it's located at PCI 2:4:0 for some odd reason, and the live cd didn't like that at all! Took me a while to figure out to run dpkg-reconfigure xserver-xorg and manually enter the 2:4:0 part, and it went fine. 

Anyway, once installed, I found that if I did *anything* to the video, it would nut up on me and quit working, and I would have to do all kinds of stuff to get it working right again.

I finally settled on boot in low graphics, make sure I have the restricted driver enabled, then run 

sudo dpkg-reconfigure xserver-xorg, chosing nvidia and of course setting PCI to 2:4:0 (let's not forget that again!), then once I'm done, I go and edit /etc/X11/xorg.conf to the version I had on the first boot when it worked right. I save it, then reboot, and I work again. All while at desktop, mind you. Doing it without X started just won't work for some retarded (which means it's me) reason. And all in that order, too. Step outside the order and it quits working.

Maybe this will help, I don't know, but good luck, and tell the frogs to quit dying off! They make Al look like he knows what he's talking about for crying out loud.

---

### Post by paulb75 on 2008-01-19
Thanks BLT, I think that does fix most of the problems. 

Oddly enough, when i retried my procedure above, my silly xserver would crash on the reboot even though it seemed fine for a few minutes. Specifically, the screen would just go dark and my monitor would go to sleep (and essentially the whole system freezes). 

Finally, I found a little gem of wisdom from the the nvidia site. By default, NvAGP is set to 3 (which means it will try the internal AGP, and something called AGPGART to get things working). That turned out to be the source of my misery!!! So I added "Option	"NvAGP"	"1""  to xorg.config:

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200 Ultra]"
    Driver         "nvidia"
	Option	"NoLogo"	"False"
	Option	"NvAGP"	"1"
EndSection

Now, I set the "NoLogo" to "False" just so I have a visual cue that my "nvidia" driver is working ("nv" and "vesa" won't load that logo). You can set it to "True" if you don't like the logo.

And it worked! If "1" hadn't worked, then I would have to try "2", or "0". One of them is bound to work. The irony is I probably wrote that line into xorg.config when I first got the system running right the first time (i copied it from someone else's xorg.conf online), then totally forgot that little edit all the times I messed up. 

If anyone has the luxury of doing a clean install, try this experiment:

1. Use the restricted-drivers manager, and let it install "nvidia-new-glx"
2. enable the driver through restricted-drivers manage, but DO NOT REBOOT YET
3. sudo gedit /etc/X11/xorg.conf
4. copy the "Section "Device"" i have up there. 
Reboot. If it fails, go into recovery mode and change the numerical value for "NvAGP"

If this quickie experiment doesn't work, let me know and I write a step-by-step procedure. I still think it's that NvAGP option that was the source of all my woes, but I don't wanna try it until I get a HD to spare. ^_^

Anyway, here's the nvidia link/instructions I got: [http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-01.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-01.html)

---

### Post by BLTicklemonster on 2008-01-19
But yours identifies itself as theNV34 [GeForce FX 5200 Ultra, whereas mine just shows the

Section "Device"
	Identifier	"vesa"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
	Videoram	128
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

(I swear, if I change the word "nvidia" it nuts up)

I'll try it anyway. Why not? :)


*Edit:
Hey, it booted. Don't see much improvement. I set it at 1. Upon reading the link, I'll test it at 3 in case it ought to use AGPART. (I get some stuttering when I scroll web pages, and I just really think I ought not to, considering that I've got a 3.3 gig processor and 500 megs of ram, plus a 128 meg video card. perhaps that will help)

*nudder Edit:
Nah, nothing. I wonder how to get my graphics to run smooth as silk? Here's me xorg.conf as of now that pertains to stuff graphically:

Section "Device"
	Identifier	"vesa"
	Driver		"nvidia"
	Busid		"PCI:2:4:0"
	Videoram	128
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        Option "NvAGP" "3"
EndSection

Section "Monitor"
	Identifier	"Nokia 446Xt"
	Option		"DPMS"
	Horizsync	30-96
	Vertrefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"vesa"
	Monitor		"Nokia 446Xt"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

I wonder if there's stuff to add there at the end?

---

### Post by paulb75 on 2008-01-22
Hi BLT, try changing your DefaultDepth to 16, and I think your graphics should run smoother.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

You might also get better performance if you rebuild the nvidia kernel. There are a few threads around on it. Here's a link to the nvidia package I used to build a kernel, and it works GREAT!!!! And guess what--it also correctly picked the option of 'Option "NvAGP" "1"' for me. :D Rebuilding the kernel is actually quite easy and painless, and the help link above tells how to (just remember, check your kernel version using ('uname -r' in the  Terminal)

[http://www.nvidia.com/object/linux_display_ia32_1.0-8776.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8776.html)

and

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run)

DM, have you had any luck with your drivers? 

Incidentally, any problems with the xserver will be logged in /var/log/ and usually with a filename like Xorg.0.log or Xorg.1.log .

---

### Post by BLTicklemonster on 2008-01-22
Thanks, I'll give it all a go later today!!

---

### Post by BLTicklemonster on 2008-01-22
Wow, much better, thanks!

---

### Post by paulb75 on 2008-01-23
No worries! I suggested the DefaultDepth 16 which is effectively 65536 colors, as opposed to Depth 24 (16.7 million colors). It seems to me you've got the right drivers, but maybe the card is a bit short on memory. For 256 colors, Depth=8.

If you want to rebuild the nvidia kernel from scratch, here's a good procedure.

[http://ubuntuforums.org/showthread.php?t=497284&highlight=build+NVIDIA+kernel](http://ubuntuforums.org/showthread.php?t=497284&highlight=build+NVIDIA+kernel)

I had to reboot though to make everything register, but it works fine and its hassle-free. 

Now I'm gonna try some serious tweaking. :D 

I hope this helps anyone else with NVIDIA problems!

---

### Post by BLTicklemonster on 2008-01-23
Wow, that totally messes up the display colors in Unreal Tournament, even though the ini file for the game shows 16 bit for the display. But my fps in the game has increased, and glxgears runs 50 percent faster than before (1500s as opposed to 1000s). I can live with the UT thing for sure.

---

