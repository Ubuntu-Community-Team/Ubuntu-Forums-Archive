---
title: "out of frequency box with 7.10"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by anilbhx on 2008-03-13
I started off with 7.04 then upgraded online to 7.10.. The problem in the subject did not exist. 
For certain reasons I had to reinstall 7.10 . I used a Live Cd. 
Now a box comes during booting showing out of frequency error . 
Hf- 63.9Khz Vf- 60hz
range hf = 33-54khz Vf=...
What can I check ?

---

### Post by rklauco on 2008-03-13
Probably, the autodetection of your monitor failed.
Try to run following command in terminal (switch using CTRL+ALT+F1):
```
sudo dpkg-reconfigure xserver-xorg
```
in terminal. The last part will be the monitor settings - choose advanced and set appropriate values. If you have LCD screen, I recommend to set the frequency to 60Hz max. as that is usualy the best refresh rate for LCD screens.
After this command finishes, try to execute 
```
sudo /etc/init.d/gdm restart
```
That should start the graphics with new resolution and refresh rate.

---

### Post by anilbhx on 2008-03-13
Thank you . I did both things .... no luck ..

---

### Post by rklauco on 2008-03-13
No luck means you are still having the frequency issues?
If you do, please, send the xorg.conf here and also, please, send the monitor maker/model.
That should give us some clue...

---

### Post by anilbhx on 2008-03-15
One more thing . The message does not appear when I start with recovery more. 
Here is the xorg.log.
Will post the xorg.conf file too. Thank you again. 

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ubuntu1 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 15 10:07:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "500G"
(**) |   |-->Device "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.2
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1849,3156 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1849,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1849,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1849,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1849,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1849,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1849,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1849,3059 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1849,3065 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 5333,8d04 card 1849,8d04 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xcfc00000 - 0xdfbfffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xdfe80000/19, 0xd0000000/27, BIOS @ 0xdfe70000/16
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [1] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [2] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [3] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [4] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [5] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [6] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [7] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [8] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [9] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [10] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [11] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [12] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [13] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [1] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [2] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [3] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [4] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [5] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [6] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [7] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [8] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [9] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [10] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [11] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [12] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [13] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [5] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [6] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [7] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [8] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [9] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [10] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [13] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [14] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [15] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [16] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [17] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [18] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [19] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
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
    compiled for 1.3.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.3.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 2.1.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.2.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.2.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) SAVAGE: driver (version 2.1.2) for S3 Savage chipsets: Savage4,
    Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
    Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
    Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
    SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
    SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
    SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01:00:0
(--) Chipset ProSavageDDR found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [5] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [6] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [7] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [8] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [9] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [10] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [13] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [14] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [15] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [16] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [17] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [18] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [19] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [5] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [6] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [7] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [8] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [9] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [10] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [11] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [12] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [13] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [17] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [18] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [19] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [20] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [21] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [22] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
    [23] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [24] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.2
(**) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.2
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(--) SAVAGE(0): Chip: id 8d04, "ProSavage DDR-K"
(--) SAVAGE(0): Engine: "ProSavageDDR"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(==) SAVAGE(0): Using AGP 1x mode
(==) SAVAGE(0): Using 16 MB AGP aperture
(==) SAVAGE(0): Write-combining range (0xd0000000,0x8000000)
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  32768k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" removed.
(II) SAVAGE(0): Manufacturer: GSM  Model: 3b1b  Serial#: 6264
(II) SAVAGE(0): Year: 2003  Week: 5
(II) SAVAGE(0): EDID Version: 1.3
(II) SAVAGE(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) SAVAGE(0): Signal levels configurable
(II) SAVAGE(0): Sync:  Separate
(II) SAVAGE(0): Max H-Image Size [cm]: horiz.: 28  vert.: 21
(II) SAVAGE(0): Gamma: 2.76
(II) SAVAGE(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SAVAGE(0): First detailed timing not preferred mode in violation of standard!(II) SAVAGE(0): redX: 0.642 redY: 0.329   greenX: 0.272 greenY: 0.604
(II) SAVAGE(0): blueX: 0.142 blueY: 0.062   whiteX: 0.282 whiteY: 0.298
(II) SAVAGE(0): Supported VESA Video Modes:
(II) SAVAGE(0): 720x400@70Hz
(II) SAVAGE(0): 640x480@60Hz
(II) SAVAGE(0): 640x480@67Hz
(II) SAVAGE(0): 640x480@72Hz
(II) SAVAGE(0): 640x480@75Hz
(II) SAVAGE(0): 800x600@56Hz
(II) SAVAGE(0): 800x600@60Hz
(II) SAVAGE(0): 800x600@72Hz
(II) SAVAGE(0): 800x600@75Hz
(II) SAVAGE(0): 832x624@75Hz
(II) SAVAGE(0): 1024x768@87Hz (interlaced)
(II) SAVAGE(0): 1024x768@60Hz
(II) SAVAGE(0): Manufacturer's mask: 0
(II) SAVAGE(0): Supported Future Video Modes:
(II) SAVAGE(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) SAVAGE(0): #1: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) SAVAGE(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) SAVAGE(0): #3: hsize: 720  vsize 405  refresh: 70  vid: 51771
(II) SAVAGE(0): #4: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) SAVAGE(0): #5: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) SAVAGE(0): #6: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) SAVAGE(0): #7: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) SAVAGE(0): Supported additional Video Mode:
(II) SAVAGE(0): clock: 65.0 MHz   Image Size:  270 x 200 mm
(II) SAVAGE(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) SAVAGE(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) SAVAGE(0): Supported additional Video Mode:
(II) SAVAGE(0): clock: 56.2 MHz   Image Size:  270 x 200 mm
(II) SAVAGE(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) SAVAGE(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) SAVAGE(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 54 kHz, PixClock max 70 MHz
(II) SAVAGE(0): Monitor name: 500G
(II) SAVAGE(0): EDID (in hex):
(II) SAVAGE(0):     00ffffffffffff001e6d1b3b78180000
(II) SAVAGE(0):     050d0103781c15b0e85f45a454459a24
(II) SAVAGE(0):     10484cbff8003140314f31593bca4540
(II) SAVAGE(0):     454f4559614064190040410026301888
(II) SAVAGE(0):     36000ec810000018f91520f830581f20
(II) SAVAGE(0):     204013000ec81000001e000000fd0032
(II) SAVAGE(0):     781e3607000a202020202020000000fc
(II) SAVAGE(0):     00353030470a20202020202020200032
(II) SAVAGE(0): Using EDID range info for horizontal sync
(II) SAVAGE(0): Using EDID range info for vertical refresh
(II) SAVAGE(0): Printing DDC gathered Modelines:
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) SAVAGE(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) SAVAGE(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) SAVAGE(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) SAVAGE(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) SAVAGE(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) SAVAGE(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(II) SAVAGE(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) SAVAGE(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) SAVAGE(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) SAVAGE(0): Modeline "640x480"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
(II) SAVAGE(0): Modeline "640x480"   30.75  640 664 728 816  480 483 487 504 -hsync +vsync
(II) SAVAGE(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) SAVAGE(0): Modeline "720x405"   26.50  720 744 808 896  405 408 413 425 -hsync +vsync
(II) SAVAGE(0): Modeline "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
(II) SAVAGE(0): Modeline "800x600"   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync
(II) SAVAGE(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) SAVAGE(0): Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) SAVAGE(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync
(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 2496x1428 TFT LCD panel detected but not active
(--) SAVAGE(0): Found 13 modes at this depth:
    [10e] 320 x 200, 70Hz
    [133] 320 x 240, 72Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [11d] 640 x 400, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz, 160Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 100Hz, 130Hz
    [17a] 1280 x 768, 60Hz
    [14f] 1280 x 960, 60Hz, 85Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 100Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [122] 1600 x 1200, 60Hz
(II) SAVAGE(0): 500G: Using hsync range of 30.00-54.00 kHz
(II) SAVAGE(0): 500G: Using vrefresh range of 50.00-120.00 Hz
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 75Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): Chose mode 14f at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 14f at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1792x1344 60Hz.
(II) SAVAGE(0): Not using default mode "1792x1344" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1856x1392 60Hz.
(II) SAVAGE(0): Not using default mode "1856x1392" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1440 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1440" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(--) SAVAGE(0): Chose mode 17a at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x768" (mode clock too high)
(--) SAVAGE(0): No suitable BIOS mode found for 640x384 60Hz.
(II) SAVAGE(0): Not using default mode "640x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x800 59Hz.
(II) SAVAGE(0): Not using default mode "1280x800" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 1152x768 54Hz.
(II) SAVAGE(0): Not using default mode "1152x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x384 54Hz.
(II) SAVAGE(0): Not using default mode "576x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 85Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 60Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1440x900 60Hz.
(II) SAVAGE(0): Not using default mode "1440x900" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 60Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1600x1024 59Hz.
(II) SAVAGE(0): Not using default mode "1600x1024" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 60Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 60Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 72Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 72Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 70Hz.
(II) SAVAGE(0): Not using driver mode "720x400" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using driver mode "832x624" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using driver mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 720x405 69Hz.
(II) SAVAGE(0): Not using driver mode "720x405" (no mode of this name)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using driver mode "0x0" (illegal horizontal timings)
(II) SAVAGE(0): Not using mode "1280x1024" (no mode of this name)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using mode "720x400" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) SAVAGE(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) SAVAGE(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) SAVAGE(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(**) SAVAGE(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Driver mode "1024x768": 63.5 MHz, 47.8 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
(**) SAVAGE(0):  Driver mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) SAVAGE(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) SAVAGE(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) SAVAGE(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) SAVAGE(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 49.0 MHz, 47.1 kHz, 74.9 Hz
(II) SAVAGE(0): Modeline "800x600"   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SAVAGE(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 38.2 MHz, 37.4 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
(**) SAVAGE(0):  Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) SAVAGE(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SAVAGE(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SAVAGE(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SAVAGE(0):  Driver mode "640x480": 30.8 MHz, 37.7 kHz, 74.8 Hz
(II) SAVAGE(0): Modeline "640x480"   30.75  640 664 728 816  480 483 487 504 -hsync +vsync
(**) SAVAGE(0):  Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) SAVAGE(0):  Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) SAVAGE(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(**) SAVAGE(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) SAVAGE(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) SAVAGE(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) SAVAGE(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) SAVAGE(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) SAVAGE(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) SAVAGE(0): Display dimensions: (280, 210) mm
(**) SAVAGE(0): DPI set to (92, 92)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xd0000000 - 0xd7ffffff (0x8000000) MS[B]
    [1] 0    0    0xdfe80000 - 0xdfefffff (0x80000) MS[B]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [6] -1    0    0xdffffd00 - 0xdffffdff (0x100) MX[B]
    [7] -1    0    0xdffffe00 - 0xdffffeff (0x100) MX[B]
    [8] -1    0    0xdfffff00 - 0xdfffffff (0x100) MX[B]
    [9] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [10] -1    0    0xdfe70000 - 0xdfe7ffff (0x10000) MX[B](B)
    [11] -1    0    0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
    [12] -1    0    0xdfe80000 - 0xdfefffff (0x80000) MX[B](B)
    [13] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [14] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [15] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [18] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [19] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [20] -1    0    0x0000fc00 - 0x0000fc0f (0x10) IX[B]
    [21] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[B]
    [22] -1    0    0x0000e400 - 0x0000e41f (0x20) IX[B]
    [23] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[B]
    [24] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
    [25] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [26] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(==) SAVAGE(0): Write-combining range (0xd0000000,0x8000000)
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) SAVAGE(0): [drm] loaded kernel module for "savage" driver
(II) SAVAGE(0): [drm] DRM interface version 1.3
(II) SAVAGE(0): [drm] created "savage" driver at busid "pci:0000:01:00.0"
(II) SAVAGE(0): [drm] added 8192 byte SAREA at 0xf8d06000
(II) SAVAGE(0): [drm] mapped SAREA 0xf8d06000 to 0xa793e000
(II) SAVAGE(0): [drm] framebuffer handle = 0xd0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3116; Card 0x5333/0x8d04]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] command DMA handle = 0xe0000000
(II) SAVAGE(0): [agp] agpTextures handle = 0xe0100000
(II) SAVAGE(0): [drm] aperture handle = 0xd2000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x33c3a000
(II) SAVAGE(0): [drm] Status page mapped at 0xa793d000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:1572864 
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x0195f000 
(II) SAVAGE(0): textureSize:0x0195f000 
(II) SAVAGE(0): textureOffset:0x00680000 
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 25980 kb for textures at offset 0x680000
(II) SAVAGE(0): Using 1023 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Image Writes
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        28 128x128 slots
        7 256x256 slots
(==) SAVAGE(0): Backing store disabled
(**) Option "dpms"
(**) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]    reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]    reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]    sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]    chipset:0x00000000
(II) SAVAGE(0): [junkers]    sgram:0x00000000
(II) SAVAGE(0): [junkers]    frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    frontOffset:0x00000000
(II) SAVAGE(0): [junkers]    frontPitch:0x00000800
(II) SAVAGE(0): [junkers]    backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    backOffset:0x00380000
(II) SAVAGE(0): [junkers]    backPitch:0x00000800
(II) SAVAGE(0): [junkers]    depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    depthOffset:0x00500000
(II) SAVAGE(0): [junkers]    depthPitch:0x00000800
(II) SAVAGE(0): [junkers]    textureOffset:0x00680000
(II) SAVAGE(0): [junkers]    textureSize:0x0195f000
(II) SAVAGE(0): [junkers]    textureSize:0x0195f000
(II) SAVAGE(0): [junkers]    logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]    agp:handle:0x00000001
(II) SAVAGE(0): [junkers]    agp:offset:0x01000000
(II) SAVAGE(0): [junkers]    agp:size:0x01000000
(II) SAVAGE(0): [junkers]    agp:map:0x00000000
(II) SAVAGE(0): [junkers]    registers:handle:0xdfe80000
(II) SAVAGE(0): [junkers]    registers:offset:0x00000000
(II) SAVAGE(0): [junkers]    registers:size:0x00080000
(II) SAVAGE(0): [junkers]    registers:map:0x00000000
(II) SAVAGE(0): [junkers]    status:handle:0x33c3a000
(II) SAVAGE(0): [junkers]    status:offset:0x00000000
(II) SAVAGE(0): [junkers]    status:size:0x00001000
(II) SAVAGE(0): [junkers]    status:map:0xa793d000
(II) SAVAGE(0): [junkers]    agpTextures:handle:0xe0100000
(II) SAVAGE(0): [junkers]    agpTextures:offset:0x00100000
(II) SAVAGE(0): [junkers]    agpTextures:size:0x00f00000
(II) SAVAGE(0): [junkers]    apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]    logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]    cmdDma:handle:0xe0000000
(II) SAVAGE(0): [junkers]    cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]    cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]    cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]    chipset:0x00000006
(II) SAVAGE(0): [junkers]    width:0x00000400
(II) SAVAGE(0): [junkers]    height:0x00000300
(II) SAVAGE(0): [junkers]    mem:0x02000000
(II) SAVAGE(0): [junkers]    cpp:2
(II) SAVAGE(0): [junkers]    zpp:2
(II) SAVAGE(0): [junkers]    agpMode:1
(II) SAVAGE(0): [junkers]    bufferSize:65536
(II) SAVAGE(0): [junkers]    frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    frontOffset:0x00000000
(II) SAVAGE(0): [junkers]    backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    backOffset:0x00380000
(II) SAVAGE(0): [junkers]    depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]    depthOffset:0x00500000
(II) SAVAGE(0): [junkers]    textureOffset:0x00680000
(II) SAVAGE(0): [junkers]    textureSize:0x01800000
(II) SAVAGE(0): [junkers]    logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]    agpTextureHandle:0xe0100000
(II) SAVAGE(0): [junkers]    agpTextureSize:0x00f00000
(II) SAVAGE(0): [junkers]    logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers]    apertureHandle:0xd2000000
(II) SAVAGE(0): [junkers]    apertureSize:0x05000000
(II) SAVAGE(0): [junkers]    aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]    statusHandle:0x33c3a000
(II) SAVAGE(0): [junkers]    statusSize:0x00001000
(II) SAVAGE(0): [junkers]    sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

---

### Post by anilbhx on 2008-03-15
Here is the xorg.conf file. 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Driver        "savage"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "500G"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Monitor        "500G"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1024x768" "800x600" "720x450" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection

---

### Post by anilbhx on 2008-04-24
I am reposting my earlier query . 
I had got the following reply and it seemed that this would solve the problem . 
But it did not.
------ Here is the earlier query again ----
I started off with 7.04 then upgraded online to 7.10.. The problem in the subject did not exist. 
For certain reasons I had to reinstall 7.10 . I used a Live Cd. 
Now a box comes during booting showing out of frequency error . 
Hf- 63.9Khz Vf- 60hz
range hf = 33-54khz Vf=50-120
The manufacturer of the Monitor is LG Electronics. 

Repeat . This problem was not there with Ubuntu 7.04 . It did not appear even when this was upgraded to 7.10. 

It appeared when I deleted and reinstalled 7.10 from a live CD. And just refuses to go . 
It also does NOT appear when I choose recovery mode at start up !!
What can I check ?
--------------------

                                                                              __________________
> **rklauco said:**
> Probably, the autodetection of your monitor failed.
Try to run following command in terminal (switch using CTRL+ALT+F1):
```
sudo dpkg-reconfigure xserver-xorg
```in terminal. The last part will be the monitor settings - choose advanced and set appropriate values. If you have LCD screen, I recommend to set the frequency to 60Hz max. as that is usualy the best refresh rate for LCD screens.
After this command finishes, try to execute 
```
sudo /etc/init.d/gdm restart
```That should start the graphics with new resolution and refresh rate.

---

### Post by hariprs on 2008-04-24
Hi,

Easy to fix, here's how:

Boot normally, when you get to a login screen don't login, instead press ctrl+alt+F2 to get to a console, login then enter the following:
```
sudo nano /etc/usplash.conf
```

if nano is not installed then:
```
sudo apt-get install nano
```

edit the file to match YOUR resolution. Here's an example:

I want a resolution of 1680x1050:
```
# Usplash configuration file
xres=1680
yres=1050
```

save the file, crtl-o, then exit, crtl-x, then enter:
```
sudo dpkg-reconfigure usplash
```

this will create a new initrd.img file with the correct resolution for your monitor, then
```
sudo reboot
```

---

### Post by AndyCee on 2008-04-25
Thanks, that worked beautifully for me.

---

### Post by anilbhx on 2008-04-30
Thanks . Hope it will work for me too. Will try now.

---

