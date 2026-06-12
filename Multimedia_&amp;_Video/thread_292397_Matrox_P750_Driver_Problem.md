---
title: "Matrox P750 Driver Problem"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by dmBriarwood on 2006-11-03
I recently purchased a 19" wide screen monitor to replace my old CRT.  Previously I used default drivers - but the quality on the wide screen is very poor.  To solve the problem, I am trying to install the proprietary drivers for my video card.  

My monitor is a Hanns-G HW192D (19" widescreen).  According to the manual,  the recommended resolution is 1440x900 at 60Hz.

After repeated attempts to install first the latest driver from [http://www.tuxx-home.at/](http://www.tuxx-home.at/) and the Matrox technical support site [http://www.matrox.com/graphics/en/corpo/support/drivers/driverList.php](http://www.matrox.com/graphics/en/corpo/support/drivers/driverList.php)I receive this error:

=======================================
   Matrox Linux Driver Install Script
========================================

./install.sh: line 122: g++: command not found
ldd: ./confapp.bin: No such file or directory
Currently installed driver is the same as the installer file.
X server driver not installed.

Messages are being logged in file /tmp/make.log,
this might take some time.

Compiling mtx.ko ... done.

Currently installed kernel module is the same as the installer file.
Kernel module not installed.

___

Unfortunately I've reached the limit of my "under-the-hood" monkeying around.  I would sure appreciate some insight and advice on how to configure the Matrox driver on my Ubuntu distro.

Below I am pasting more information: my system, kernel version, X version, and X log file.

Thanks very much
Dave


____
My system has:

AMD Athlon XP 3200+ Barton 400 FSB
Asus A7V600 Socket A Mainboard
Matrox P750 DDR 64MB Dual
Ubuntu-DapperDrake

_______
Here is some other information I've seen asked for in various forum posts:

$ uname -r
2.6.15-27-386

$ X -version

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Dapper-Desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

$ lspci | grep -i matrox
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. Millenium P650/P750 (rev 02)

$


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Dapper-Desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  3 16:40:43 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "P95f+-2"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.8
    X.Org XInput driver : 0.5
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10b7,1700 card 1043,80eb rev 12 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 1102,0002 card 1102,8067 rev 0a class 04,01,00 hdr 80
(II) PCI: 00:0a:1: chip 1102,7002 card 1102,0020 rev 0a class 09,80,00 hdr 80
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 01:00:0: chip 102b,2537 card 102b,1820 rev 02 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xf3000000 - 0xf3efffff (0xf00000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xf3f00000 - 0xf7ffffff (0x4100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) Matrox Graphics, Inc. Millenium P650/P750 rev 2, Mem @ 0xf4000000/26, 0xf3000000/13, BIOS @ 0xf3fe0000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [1] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [2] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [3] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [4] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [5] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [6] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [7] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [8] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [9] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [10] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [11] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [12] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [13] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [14] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [15] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [16] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [17] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [18] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [19] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [1] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [2] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [3] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [4] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [5] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [6] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [7] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [8] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [9] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [10] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [11] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [12] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [13] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [14] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [15] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [16] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [17] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [18] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [19] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [5] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [8] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [9] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [12] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [13] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [14] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [15] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [16] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [17] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [18] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [19] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [20] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [21] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [22] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [23] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [24] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [25] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.0.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 6.99.99.904, module version = 1.0.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [5] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [8] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [9] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [12] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [13] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [14] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [15] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [16] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [17] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [18] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [19] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [20] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [21] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [22] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [23] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [24] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [25] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [5] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [8] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [9] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [10] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [11] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [12] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [17] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [18] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [19] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [21] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [22] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [24] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [25] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [26] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [27] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [28] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [29] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [30] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: Matrox Graphics Inc.
(II) VESA(0): VESA VBE OEM Software Rev: 1.3
(II) VESA(0): VESA VBE OEM Vendor: Matrox
(II) VESA(0): VESA VBE OEM Product: Matrox Sundog
(II) VESA(0): VESA VBE OEM Product Rev: 00
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: HSD  Model: 8992  Serial#: 16843009
(II) VESA(0): Year: 2006  Week: 32
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
(II) VESA(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 640  vsize 480  refresh: 66  vid: 17969
(II) VESA(0): #1: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VESA(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #6: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) VESA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) VESA(0): Ranges: V min: 49  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) VESA(0): Monitor name: HW192D
(II) VESA(0): Serial No: 632GS3CY01547
(II) VESA(0): Searching for matching VESA mode(s):

<I removed the modes to post length limits>

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): P95f+-2: Using default hsync range of 30.00-80.00 kHz
(II) VESA(0): P95f+-2: Using default vrefresh range of 49.00-75.00 Hz
(II) VESA(0): Not using mode "2048x1536" (no mode of this name)
(II) VESA(0): Not using mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using mode "1792x1344" (no mode of this name)
(II) VESA(0): Not using mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using mode "832x624" (no mode of this name)
(II) VESA(0): Not using mode "720x400" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(--) VESA(0): Display dimensions: (410, 260) mm
(--) VESA(0): DPI set to (79, 100)
(WW) (1280x1024,P95f+-2) mode clock 157.5MHz exceeds DDC maximum 140MHz
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf2000000 - 0xf20000ff (0x100) MX[b]
    [5] -1    0    0xf2800000 - 0xf2803fff (0x4000) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xf3fe0000 - 0xf3ffffff (0x20000) MX[b](B)
    [8] -1    0    0xf3000000 - 0xf3001fff (0x2000) MX[b](B)
    [9] -1    0    0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
    [10] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [11] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [12] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x00008400 - 0x0000841f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000881f (0x20) IX[b]
    [17] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [18] -1    0    0x00009400 - 0x0000941f (0x20) IX[b]
    [19] -1    0    0x00009800 - 0x0000980f (0x10) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [21] -1    0    0x0000a400 - 0x0000a40f (0x10) IX[b]
    [22] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [24] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [25] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [26] -1    0    0x0000d000 - 0x0000d007 (0x8) IX[b]
    [27] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [28] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [29] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [30] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: Matrox Graphics Inc.
(II) VESA(0): VESA VBE OEM Software Rev: 1.3
(II) VESA(0): VESA VBE OEM Vendor: Matrox
(II) VESA(0): VESA VBE OEM Product: Matrox Sundog
(II) VESA(0): VESA VBE OEM Product Rev: 00
(II) VESA(0): virtual address = 0xb68aa000,
    physical address = 0xf4000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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

---

### Post by dmBriarwood on 2006-11-07
*I started this message to outline the method that worked for me - it seems I've gone on a bit at first - but I've described the procedure generally at the bottom...*

So - I found this experience incredibally frustrating - web posts here, on the Matrox site and elsewhere are missing just enough information to make it really difficult for a relatively inexperienced command line user like me to solve this problem.  Thankfully I had the help of some friends with much more experience than myself who provided hints and tips that lead me to the promised land.

It flat out shouldn't be this difficult.  (although I know that Ubuntu is an absolute dream compared to some current and previous distributions). I know the video card companies are completely to blame for all the trouble with the drivers - but I think managers of the bigger linux distributions should spend more time making user-friendly how-tos for less experienced users.  I know this is a work in progress - and documentation is much better than it used to be.  Still, user-friendliness is the key to widespread use (even if the heavens and the earth were created using the command line!).  Maybe Ubuntu should go from six-month to yearly releases and spend the second six months of the year testing and perfecting the release, developing how-to's for the wide range of chips, boards, peripherals, and binary blobs for proprietary drivers - all to the end that Ubuntu is easier to use, easier to install, and easier to upgrade.  I'd love to see: 

1. Some kind of hardware optimizing software that chooses the best packages based on my system construction.  I have an AMD processor - there are kernal packages out there that make Ubuntu markedly faster - same goes for video cards, and other internal components.  This doesn't have to happen on install - just a centralized place where I can look to optimize my system's performance.

2. Scaffolding between distributions needs more attention.  Upgrading a distribution is a pain in the butt - it is really time consuming.  I've not tried the synaptic way - early on in my linux experience I was told that I should always re-install.  I've also seen posts where people have set up their /home folders on different partitions to avoid losing stuff - but I've never been able to get it right.  This could be just my issue, but usually if one person doesn't get it there are probably others.  

Wouldn't it be great if there was an upgrade program you could run that would back up all your programs and their key bits onto a cd/dvd, wipe the drive, install the new distribution and prompt you to put your backup disc in the drive and set everything up for you?  It is really time consuming to re-configure things every six months when new distributions come out - it's a serious disincentive for getting someone to try Ubuntu.

Anyway - I've gone on long enough - I hope my comments aren't taken as angry - they're not meant to be.  I believe strongly in Linux and the open source movement - and I absolutely love Ubuntu.  So much progress has been made in a relatively short period of time - but the recent problems with X, and Ubuntu's problems with 6.10 and this gong-show of a driver installation process make me think that a second look needs to be taken at the timing of the releases, the testing distributions go through before release, and how the support networks are structured for the average user.  At different points over the past couple of weeks this driver experience had me seriously considering buying an older video card - (although my current Matrox P750 is 3 years old - how much older would I have to go?) I even toyed with the idea of switching to XP - but I know that is an illusion.

So - I got my Matrox P750 DH 64M single display video card working on my new 19" wide screen monitor (at the recommended 1440x900 @ 60Hz) by:

1.  Performing a fresh installation of Dapper Drake 6.06 after my intitial attempts to install the driver broke my system.

2. Obtained the latest beta driver (1.4.4.3) from a sticky post on the Matrox Forum website.

3. Installed the K7 kernel package using synaptic.
4. Installed the K7 kernel header package.
5. Installed "build-essentials" package

6. I then followed the instructions found in Ubuntu Hacks (p200) from the "sudo sh..." line.
7. Backed up the libGL file as outlined by the two commands there
8. Modified the Xorg.conf file using gedit as root
9. Changed "device" "driver" to mtx
10. Added "1440x900" to each of the resolutions lines in Xorg.conf
11. Saved Xorg.conf, rebooted, and set my resolution to 1440x900 @60Hz.

I have a line by line procedure file that I will clean up and post in the next few days.  Any questions, don't hesitate to ask.  Sorry for bending your ear there!    

dm

---

