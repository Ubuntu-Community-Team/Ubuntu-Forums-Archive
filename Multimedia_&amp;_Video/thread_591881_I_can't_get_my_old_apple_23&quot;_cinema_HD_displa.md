---
title: "I can't get my old apple 23&quot; cinema HD display work :("
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by sir5245 on 2007-10-25
I have an old apple cinema HD display (The plastic one not the silver aluminium one) and nVidia GeForce FX 5700LE. I just can't get it work. After boot up the light on the front of the monitor is flashing (repeating sequence of three short flashes), it means the input is in the wrong video format. I have no idea for the situation. Can anyone help me..
The following is my Xorg.0.log & xorg.conf
Thanks a lot.
(I install ubuntu 7.10)
> 
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux arthur-Ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 25 22:15:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "AppleHD"
(**) |   |-->Device "nVidia Corporation NV36 [GeForce FX 5700LE]"
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
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80f2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,80f3 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0343 card 1043,81a2 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:05:0: chip 10b7,1700 card 1043,80eb rev 12 class 02,00,00 hdr 00
(II) PCI: 02:0d:0: chip 1131,7133 card 185b,c100 rev 10 class 04,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xf6000000 - 0xf7efffff (0x1f00000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe0000000 - 0xf4ffffff (0x15000000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[b]
    [1] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [2] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [3] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xf7f00000 - 0xfbffffff (0x4100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV36 [GeForce FX 5700LE] rev 161, Mem @ 0xf6000000/24, 0xe0000000/28, BIOS @ 0xf7ee0000/17
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
(II) PCI Memory resource overlap reduced 0x54000000 from 0x57ffffff to 0x53ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [1] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [2] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [3] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [4] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [5] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [6] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [7] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [8] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [9] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [10] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [11] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [12] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [13] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [14] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [15] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [16] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [17] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [18] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [19] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [20] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [21] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [22] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [1] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [2] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [3] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [4] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [5] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [6] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [7] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [8] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [9] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [10] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [11] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [12] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [13] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [14] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [15] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [16] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [17] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [18] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [19] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [20] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [21] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [22] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
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
    [4] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [5] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [6] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [7] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [8] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [9] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [10] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [11] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [17] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [18] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [19] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [20] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [21] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [22] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [23] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [24] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [25] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [26] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [27] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [28] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.3.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
    compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [5] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [6] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [7] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [8] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [9] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [10] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [11] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [17] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [18] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [19] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [20] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [21] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [22] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [23] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [24] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [25] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [26] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [27] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [28] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [5] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [6] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [7] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [8] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [9] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [10] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [11] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [13] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [20] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [21] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [22] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [23] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [24] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [25] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [26] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [27] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [28] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [29] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [30] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [31] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
    [32] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [33] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5700LE (NV36) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.46.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5700LE at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Apple CinemaHD Display (DFP-0)
(--) NVIDIA(0): Apple CinemaHD Display (DFP-0): 150.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple CinemaHD Display (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (33, 39); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xe0000000 - 0xefffffff (0x10000000) MX[b]
    [1] 0    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xf7ff7800 - 0xf7ff7fff (0x800) MX[b]
    [7] -1    0    0xf7ffc000 - 0xf7ffffff (0x4000) MX[b]
    [8] -1    0    0xf5fff400 - 0xf5fff4ff (0x100) MX[b]
    [9] -1    0    0xf5fff800 - 0xf5fff9ff (0x200) MX[b]
    [10] -1    0    0x50000000 - 0x500003ff (0x400) MX[b]
    [11] -1    0    0xf5fffc00 - 0xf5ffffff (0x400) MX[b]
    [12] -1    0    0x54000000 - 0x53ffffff (0x0) MX[b]O
    [13] -1    0    0xf7ee0000 - 0xf7efffff (0x20000) MX[b](B)
    [14] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [15] -1    0    0xf6000000 - 0xf6ffffff (0x1000000) MX[b](B)
    [16] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [17] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [18] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [20] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [21] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [22] -1    0    0x0000d400 - 0x0000d43f (0x40) IX[b]
    [23] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [24] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [25] -1    0    0x0000b800 - 0x0000b80f (0x10) IX[b]
    [26] -1    0    0x0000b880 - 0x0000b883 (0x4) IX[b]
    [27] -1    0    0x0000bc00 - 0x0000bc07 (0x8) IX[b]
    [28] -1    0    0x0000c000 - 0x0000c003 (0x4) IX[b]
    [29] -1    0    0x0000c080 - 0x0000c087 (0x8) IX[b]
    [30] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [31] -1    0    0x0000d880 - 0x0000d89f (0x20) IX[b]
    [32] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [33] -1    0    0x0000d480 - 0x0000d49f (0x20) IX[b]
    [34] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [35] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "640x480"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "640x480"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
> 
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
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV36 [GeForce FX 5700LE]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    30-70
    Vertrefresh    50-160
EndSection

Section "Monitor"
    Identifier    "AppleHD"
    Option        "DPMS"
    Horizsync    28-96
    Vertrefresh    43-60
    Modeline    "1920x1200" 155.0 1920 1984 2016 2144 1200 1203 1206 1212 -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV36 [GeForce FX 5700LE]"
    Monitor        "AppleHD"
    Defaultdepth    24
    SubSection    "Display"
        Depth    24
        Modes    "1920x1200" "1680x1050" "1280x960" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
EndSection


---

