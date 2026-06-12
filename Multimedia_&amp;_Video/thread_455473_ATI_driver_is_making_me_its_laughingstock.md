---
title: "ATI driver is making me its laughingstock"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by viva_cthulhu on 2007-05-26
Thanks in advance for any help, and apologies if my post proves too foolish...
ATI Radeon X1600 AGP, Feisty Fawn, Amd 2800+.
The "restriced driver" is enabled in System->Administration, and xorg.conf seems to be aware of the card and everything...
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```
Yet glxinfo says no direct rendering, and anything from glxgears to zsnes to full-screen videos slows the system to a crawl.
It's driving me insane.
The current system status comes from following several tutorials on installing xgl-beryl and from the installation of the official ATI proprietary driver (althought that one got jammed and I had to force some parameter from command line to make it work).
All these steps have, of course, been taken in a baboonlike trance of unquestioningly following the instructions from the guys on the internet.
I feel ashamed in asking for help, but it's annoying you innocent strangers or succumbing to grotesque insanity and starting to feed on roaches. Thanks in advance!

---

### Post by JordanII on 2007-05-26
Try System>Preferences>Desktop Effects and then "Enable Desktop Effects". It should then ask if you want to install the driver for your card (it works for nVidia GeForce 6100). If the screen goes white after applying don't panic, just hit Control+Alt+F2. This will go to a terminal and then type your user name and password if necessary. Type "sudo /etc/init.d/gdm stop". Then type "startx". **_WARNING: ONLY DO THIS IF YOU HAVE A FAST COMPUTER_**. 512MB of RAM is the minimum amount of RAM that I would try this on.

---

### Post by viva_cthulhu on 2007-05-26
Ok, first of all: thank you!
Tried it... it says the "Composite" extension isn't available.
I remember the various Ati [installation ]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI") [guides]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") I read insisted I disable Composite in xorg.conf - seems it carries hatred for something in the ATI driver.

---

### Post by viva_cthulhu on 2007-05-26
Also: I remember [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") is one of thoose I followed. fglrxinfo still insists I'm running on Mesa.

---

### Post by Kubunteando on 2007-05-27
I wonder why do you have 2 "Device" entries in the xorg.conf file?
I suspect the first entry is not needed, you can try to delete it (make a backup of the xorg.conf just in case).

Can you post the file: /var/log/Xorg.0.log ?
That should give some idea what is wrong...

---

### Post by viva_cthulhu on 2007-05-27
Mmh, I thought they were fishy... I tried disabling the *second* device, which resulted in x failing to boot and forcing me to restore a backup... I'll try the first!
In the meantime, here's the log... and thanks a lot!

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux krelian-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 26 23:40:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
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
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0e:0: chip 1102,0004 card 1102,005a rev 03 class 04,01,00 hdr 80
(II) PCI: 00:0e:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:0e:2: chip 1102,4001 card 1102,0010 rev 01 class 0c,00,10 hdr 80
(II) PCI: 00:0f:0: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 0000,0000 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c2 card 174b,0850 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e2 card 174b,0851 rev 00 class 03,80,00 hdr 00
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
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xde800000 - 0xdfefffff (0x1700000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xf7ffffff (0x18100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xe0000000/28, 0xdf000000/16, I/O @ 0xd800/8, BIOS @ 0xdffe0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xde800000/16
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
	[0] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[1] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[2] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[3] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[4] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[7] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[10] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[13] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[1] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[2] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[3] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[4] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[7] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[10] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[13] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
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
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[8] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[17] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[20] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[8] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[17] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[20] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e7a30
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[8] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[23] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0850)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xdf000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: HSD  Model: 899a  Serial#: 3000
(II) fglrx(0): Year: 2006  Week: 4
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.647 redY: 0.327   greenX: 0.292 greenY: 0.614
(II) fglrx(0): blueX: 0.142 blueY: 0.079   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: HU196D

```

---

### Post by viva_cthulhu on 2007-05-27
The second part (so you know the ending, who marries who etc)
```
(II) fglrx(0): Serial No: 604GA12CA3000
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0022649a89b80b0000
(II) fglrx(0): 	041001036c261e782afd56a5534a9d24
(II) fglrx(0): 	144f54adcf0081800101010101010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000fd00384b1e
(II) fglrx(0): 	500e000a202020202020000000fc0048
(II) fglrx(0): 	55313936440a202020202020000000ff
(II) fglrx(0): 	0036303447413132434133303030008c
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 31 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xdd000000 - 0xdd003fff (0x4000) MX[B]
	[9] -1	0	0xdd800000 - 0xdd8007ff (0x800) MX[B]
	[10] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[13] -1	0	0xdf000000 - 0xdf00ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde800000 - 0xde80ffff (0x10000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[26] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[28] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb73b9000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.36.5
(II) fglrx(0):     Date: Apr 17 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb73b9000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xe0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x00000404
fbarea0->box.x2 0x00000500, fbarea0->box.y2 0x00000406
icon[0].start=0x505000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x00000406
fbarea1->box.x2 0x00000500, fbarea1->box.y2 0x00000408
icon[1].start=0x508000
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
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
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
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
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by viva_cthulhu on 2007-05-28
Ok, I tried removing each of the "Device"s. Removing either causes Ubuntu tu return a "monitor not found" error and to boot in command line mode.
Restored original xorg.conf, and patiently waiting for help...

---

### Post by Kubunteando on 2007-05-28
Not a bad script, but the story has a clear error message on the log file:

"(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work"

And surprise, surprise. The error message seems to be right...at least this time.

So this means, the ATI proprietary drivers module (fglrx) does not match your installation (kernel or Xorg versions, and I would bet it is the kernel).

Since you are using Xorg 7.2, I guess you are using Ubuntu 7.04 Feisty.

How did you installed the ATI proprietary drivers?
Did you got them from Feisty Repositories or from the ATI binaries?

Usually this links should help:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Also, if you upgraded from Edgy, you may need to reinstall the ATI drivers, since the kernel version has changed. The link above should also help.

---

### Post by viva_cthulhu on 2007-05-28
Thanks a lot! I'm still in trouble - slightly bigger this time.
I had installed from **both** the repositories and the ATI binary; since I have gone through quite a few retries of the "install from the repositories" routine, I tried re-installing the ATI binaries the way your guide suggested - seems like you were right, the kernel installation ([fglrx kernel etcetera]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-401536bf91e38e3a2ffaf83fde1c32b9d773e0c5")) clearly stated it was changing version,
Trouble though - on rebooting, X goes black screen. Thought it could be a monitor issue, but it does not make too much sense, since audio seems gone too...
Command line (recovery mode) works still, xinit produces the same results though.
Looking over google for solutions to this new one... I really hope setting up linux is not so INSANELY HARD for everyone else... it's been something like a month since I installed, and I am still spending something like 10-12 hours a week configuring the thing. Feeling really weary.
Please let me know something - my system currently is dead... thanks in advance!

---

### Post by viva_cthulhu on 2007-05-28
Ok, system no longer dead - reconfigured xorg.conf to run on mesa.
Still needs help. but it's no longer urgent.
According to google, this "Black screen of Death" thing seems to affect several ATI installations, and to not have a solution...

I think we could change approach;

The regular way to install Ati drivers, through repositories, should work fine normally, no? Then, how do I remove them and all the clutter I installed in my attempts to install the ati driver?
If I just re-install the driver through the repositories, will it overwrite the one from the ATI binaries? Because I think it's the xorg update that made it work at least (albeit producing a Black Screen of Death). Maybe placing the repository drivers in place of the binaries will do the trick...
Dunno, guessing.

Thanks again!

---

### Post by eye208 on 2007-05-29
Why not just reinstall, activate the driver from the repository, and be done with it? Yes, a full install will take another 45 minutes of your time. Removing the clutter from your current system will probably take longer.

You can test whether the driver from the repository works for you prior to installing. Just boot the Live CD in safe graphics mode, open the restricted drivers manager, mark the checkbox for the ATI driver, install, ignore the reboot request and hit Ctrl-Alt-Backspace to restart X.org. Then open a terminal and enter fglrxinfo. You will most likely see that the ATI driver is already running, with direct rendering enabled. Enter "sudo aticonfig --ovt Xv" and restart X.org again to enable Xvideo overlay extension. That's all.

Using the driver from the repository also means you need not worry about kernel updates. The driver kernel module will always be in sync with the kernel.

---

### Post by viva_cthulhu on 2007-05-29
Testing from the live cd seems an excellent idea!
Unfortunately I currently cannot test it - my livecd is a kubuntu one - I'll download the gnome version and try, although I feel guilty pumping money from that african rich guy benefactor just for testing a driver...
I seem to recall trying that solution before - the driver made linux unusable and made large portions of the windows invisible, so I turned to the web tutorials and installed from the repositories and then from ati.
I would rather not reinstall if possible - I have alreadly gone through a HUGE ammount of work to make ubuntu work like I wanted it, and I shudder at the thought of having to go through everything again...
Thanks a lot! Letting you know after I test from the livecd...

---

### Post by Kubunteando on 2007-05-29
From the repositories you may not get the last ATI driver versions.

Some more questions to put some light.

What is your ATI card model?

What is your current kernel version? You can execute "uname .a" in a console program.

Still the same error in the /var/log/Xorg.0.log file when you try the "fglrx" module?

Well, I can tell that setting up the HW acceleration in Linux is a bit tricky in ATI cards.
Once you get it running, the rest should be a piece of cake compared.

To me it took a while also to get it running, but my ATI is much older and out of support.
And the ATI drivers did not work well.

---

### Post by eye208 on 2007-05-30
> **viva_cthulhu said:**
> Testing from the live cd seems an excellent idea!
Unfortunately I currently cannot test it - my livecd is a kubuntu one
The Kubuntu Live CD should work as well. If there's no restricted drivers manager on Kubuntu you can use Adept or apt-get instead. The following steps should work:

1. Start Live CD in safe graphics mode.
2. Open Adept and install "xorg-driver-fglrx".
3. Open a terminal and run "sudo aticonfig --initial --ovt Xv".
4. Run "sudoedit /etc/X11/xorg.conf" and add the following lines at the end of the file:
```
Section "Extensions"
    Option "NoComposite"
EndSection
```
5. Save the file, close the terminal, then press Ctrl-Alt-Backspace to restart X.org.
6. Run "fglrxinfo". The fglrx driver should be up and running with direct rendering enabled.

---

### Post by viva_cthulhu on 2007-06-07
First of all, apologies for late posting. I was away from the involved machine for a few days.
> The Kubuntu Live CD should work as well. If there's no restricted drivers manager on Kubuntu you can use Adept or apt-get instead.
I cursed aloud in shame for not coming up with this on my own.
The installation didn't work - glitches made most of the contents of the windows disappear made screen refreshing basically impossibile.
Managed to blindly make a couple of screenshots - will post them as soon as I get back there, I hope tonight...

---

### Post by viva_cthulhu on 2007-06-07
I forgot - in the meantime, thanks for the help... it's really appreciated.

---

### Post by viva_cthulhu on 2007-06-07
Also forgot - Kubuntuendo I didn't see your post!
Once again, I'll reply tonight once I get to the machine and post the screenshots - for what I can tell:
> What is your ATI card model?
X1600
> What is your current kernel version? You can execute "uname .a" in a console program.
I remember a 2.something.10 but might be wishful thinking. Tonight it is for that.
I have feisty, but it was updated from edgy. Wouldn't know if the kernel remained the same but would guess not.
> Well, I can tell that setting up the HW acceleration in Linux is a bit tricky in ATI cards.
It hadn't escaped my notice : )
Well, I'll try patiently. Even as it is, I like linux too much to switch back.
Thanks again!

---

### Post by Bablefish on 2007-06-07
I have been using Edgy and it seems to work for me

---

### Post by viva_cthulhu on 2007-06-07
Ok, now for the thrilling conclusion:
[LIST]
[*][Screenshots of "teh glitch"]("http://www.onlinecomics.altervista.org/extra/ragni.html"). Hope it's not too scaled down - I thought I was going to upload it to the forum... Perhaps KDE's default theme is only slightly less scary than the glitch.
[*]My Kernel: "Linux krelian-desktop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux" (so I got it completely wrong the first time...). Should be the default.
[*]Xorg.0.log never mentions fxgl... of course, they are not loaded, since the last time they produced the infamous "black screen". Were I to purposely restart the system so it creates a Black Screen of Death, would Xorg.0.log still show what went wrong?
[/LIST]
As alwais, thanks again... I'm being pretty annoying : )

> I have been using Edgy and it seems to work for me
There's people out there that have been successfully installed beryl on 286s...
There's people with configurations basically identical to mine that have it working fine through methods that don't work on my system repeated step by step.
 It's just me I would assume.
Damn Gypsy curses. Thought they were normal people when I ran over them.

---

### Post by Kubunteando on 2007-06-08
I would suggest still to have a look at the Xorg.0.log, even if you get the black screen the logs will be there, just copy them before restarting.

I also found this link it maybe useful (yet another way how to install it, another try):

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

This link comes directly from the ATI driver pages, maybe is more tested...

Check the troubleshooting section, there is a really interesting note I post below:

 Graphical Anomalies

This was experienced with an ATI Radeon X1600 Pro 512mb:

After following instructions for both Method 1 and Method 2, whenever the Composite Extension is disabled, the display would be almost unusable, but the fglrxinfo command would display the correct information. If the Composite Extension is re-enabled the display would be usable, but fglrxinfo would report using mesa drivers.

To resolve the problem it maybe needed to lower the AGP Aperture setting in my BIOS to 128mb (or lower worked too). The AGP Aperture was initially set to 256mb. After setting the AGP Aperture to 128mb, everything worked perfectly; the Composite Extension is disabled, fglrxinfo reports the correct drivers, and direct rendering is enabled. Some systems may require setting the AGP Aperture to the highest setting (256mb or 512mb). 

-----------------
I think this will help, but first it is needed that the fglrx module loads correctly!

You can go through the troubleshooting and see what info you can gather.
But the info above may be really useful if you have the model PRO with 512MB

---

### Post by viva_cthulhu on 2007-06-17
***IT WORKS! IT WORKS!*** OH MY GOD IT WORKS!
Oh, Gods, Finally!

Turns out: you were absolutely right kubuntuendo, it was my bios's agp aperture setting! It was set to - horror! - 64megabytes - on a 512 mb card! (it was that hint - exact description of my card: agp, 512 meg)
Funny thing - I had *read* that page. Something like thrice - it's one of the most informative pages among the top Google results. I had missed that bit!

Tried it on the livecd and on my pc right after - exactly like the easy tutorials, just turn on the "restricted drivers" thing.

Oh god, I don't know how to thank you Kubuntuendo - I'm downright *gleeful* right now! You turned me in a linux user; so far I couldn't be certain that I wouldn't go back to "that other OS where they ship drivers on a cd". Now the only one among the Great Problems I faced in changing to Ubuntu that I couldn't figure out on my own is finally - *finally*, because there's no understating how much time I have wasted on this - solved; all thanks to you!

Well... that's all. Thanks again everyone! Sorry about the rant.

---

### Post by Kubunteando on 2007-06-18
Glad to help!

Please, don't put on me having turned you into a Linux user. There is no way I will reach heaven after such a thing ;) You will understand this after a few years... :D

The Linux community is growing and growing so welcome.
Linux is not as easy as Windows, and sometimes you learn the hard way (especially with ATI cards...). But the good thing is that there is so much information and help available that you will always learn something new until you can manage by yourself.

As opposite to many people I don't think Windows is bad, on the contrary I thing their products are quite OK for beginners. But not for those who want to learn and want to know what they are doing. On the other hand Windows is too cold, close and empty, where is the people behind it? Here you have guys ready to give you some hints and help you. This is a much warmer place in my opinion...

So enjoy the community.

---

