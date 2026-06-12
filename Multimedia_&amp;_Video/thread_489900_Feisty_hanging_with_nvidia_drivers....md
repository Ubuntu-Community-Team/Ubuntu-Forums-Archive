---
title: "Feisty hanging with nvidia drivers..."
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2007-07-01
I'm not sure what the problem is, but my system seems stable when using the default 'nv' drivers under Feisty.

When I use the Restricted Drivers Manager to install the nvidia driver, things are stable for a random amount of time after installation, and then X just hangs.  I am still able to ssh from another machine, however. :-)

Here is the contents of /var/log/Xorg.0.log:
```

$ cat Xorg.0.log

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mythtv 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  1 20:44:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SAMSUNG"
(**) |   |-->Device "nVidia Corporation NV44 [GeForce 6200 LE]"
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
(II) PCI: 00:00:0: chip 10de,02f1 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 0000,0000 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 10de,cb84 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 105b,0caf rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 105b,0caf rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 105b,0caf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 105b,0caf rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 105b,0caf rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 105b,0caf rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 10de,cb84 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 10de,cb84 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:2: chip 10de,026b card 105b,0caf rev a2 class 04,01,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 105b,0caf rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 10de,0163 card 3842,c227 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:06:0: chip 104c,8023 card 105b,0caf rev 00 class 0c,00,10 hdr 00
(II) PCI: 04:07:0: chip 10b7,9055 card 10b7,9055 rev 30 class 02,00,00 hdr 00
(II) PCI: 04:08:0: chip 4444,0016 card 0070,8003 rev 01 class 04,00,00 hdr 00
(II) PCI: 04:09:0: chip 168c,0013 card 1385,5a00 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x00008000 - 0x000080ff (0x100) IX[b]
        [1] -1  0       0x00008400 - 0x000084ff (0x100) IX[b]
        [2] -1  0       0x00008800 - 0x000088ff (0x100) IX[b]
        [3] -1  0       0x00008c00 - 0x00008cff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xfdd00000 - 0xfddfffff (0x100000) MX[b]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xfdb00000 - 0xfdbfffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [1] -1  0       0x0000a400 - 0x0000a4ff (0x100) IX[b]
        [2] -1  0       0x0000a800 - 0x0000a8ff (0x100) IX[b]
        [3] -1  0       0x0000ac00 - 0x0000acff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfda00000 - 0xfdafffff (0x100000) MX[b]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xfde00000 - 0xfdefffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 3 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[b]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[b]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[b]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[b]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xfa000000 - 0xfcffffff (0x3000000) MX[b]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[b]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[b]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[b]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[b]
(II) Bus 4 non-prefetchable memory range:
        [0] -1  0       0xfdc00000 - 0xfdcfffff (0x100000) MX[b]
(II) Bus 4 prefetchable memory range:
        [0] -1  0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(--) PCI:*(3:0:0) nVidia Corporation NV44 [GeForce 6200 LE] rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(--) PCI: (4:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf4000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
        [0] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [1] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [2] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [3] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [4] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [5] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [6] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [7] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [8] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [9] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [10] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [12] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [13] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [14] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [15] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [16] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [19] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [20] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [21] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [22] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [23] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [24] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [25] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [26] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [27] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [28] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [29] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [30] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [1] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [2] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [3] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [4] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [5] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [6] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [7] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [8] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [9] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [10] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [12] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [13] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [14] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [15] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [16] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [19] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [20] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [21] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [22] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [23] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [24] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [25] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [26] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [27] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [28] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [29] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [30] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [20] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [21] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [22] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [23] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [24] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [25] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [26] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [27] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [28] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [29] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [30] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [31] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [32] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [33] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [34] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [35] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [36] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
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
        compiled for 4.0.2, module version = 1.0.9631
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
        compiled for 4.0.2, module version = 1.0.9631
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [20] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [21] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [22] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [23] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [24] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [25] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [26] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [27] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [28] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [29] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [30] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [31] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [32] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [33] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [34] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [35] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [36] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b]
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b]
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b]
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [23] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [24] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [25] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [26] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [27] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [28] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [29] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [30] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [31] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [32] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [33] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [34] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [35] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [36] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [37] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [38] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [39] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [40] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b]
        [41] 0  0       0x000003c0 - 0x000003df (0x20) IS[b]
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
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 LE at PCI:3:0:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (37, 37); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfb000000 - 0xfbffffff (0x1000000) MX[b]
        [1] 0   0       0xd0000000 - 0xdfffffff (0x10000000) MX[b]
        [2] 0   0       0xfa000000 - 0xfaffffff (0x1000000) MX[b]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [7] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[b]
        [8] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[b]
        [9] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[b]
        [10] -1 0       0xfdcff000 - 0xfdcff7ff (0x800) MX[b]
        [11] -1 0       0xfe02a000 - 0xfe02afff (0x1000) MX[b]
        [12] -1 0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [13] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [14] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [15] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [16] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [17] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[b](B)
        [18] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[b](B)
        [19] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [20] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[b](B)
        [21] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
        [22] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
        [23] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [26] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[b]
        [27] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [28] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [29] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [30] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[b]
        [31] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[b]
        [32] -1 0       0x00000960 - 0x00000967 (0x8) IX[b]
        [33] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[b]
        [34] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[b]
        [35] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [36] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [37] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [38] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [39] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [40] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [41] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [42] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [43] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
        [44] 0  0       0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Setting mode "1920x1080"
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
$ 

```And this is the contents of my xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV44 [GeForce 6200 LE]"
        Driver          "nvidia"
        Busid           "PCI:3:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "SAMSUNG"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44 [GeForce 6200 LE]"
        Monitor         "SAMSUNG"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1920x1080"     "1600x1200"     "1280x1024"    "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by mmcmonster on 2007-07-02
Can anyone help?  This happened on multiple attempts at installation on the same machine with Feisty.  I haven't tried Dapper yet on the machine.

---

### Post by mmcmonster on 2007-07-03
Any other information I can add to help figure out what the problem is?

---

### Post by mmcmonster on 2007-07-05
Bump

---

### Post by dabl on 2007-07-05
I'm no guru, but since you're not getting help, I'll take a shot.

You say the problem comes up when you switch to the Nvidia driver, but the error output appears to point to the wacom devices.  That is strange.  Is this a very new system?  If so, the packaged Nvidia driver may not be new enough to run it correctly.  May I suggest, as an experiment, (_after_ you have backed up the version of /etc/X11/xorg.conf that works with the nv driver) disabling the restricted driver (removing it from the Restricted Drivers Manager), then download and install Envy from this site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the file > envy_0.9.5-0ubuntu5_all.deb When it is downloaded to your desktop, right click on it and choose "install package" to install it.  After it is installed, it will appear in your system menu, and you can run it from there, or you can open a console window and enter ```
sudo envy -t
``` to run it in text mode.  It will install the newest Nvidia driver, and it will reconfigure xorg.conf for optimal performance.

I hope this experiment sheds a little light on your problem.  :)

---

### Post by mmcmonster on 2007-07-05
Same problem happened.  It took about 10 minutes after the reboot to crash X.  In fact, I was in the middle of posting to this thread that things were okay so far. :-)

Here is a copy of /var/log/Xorg.0.log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mythtv 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  5 12:11:04 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SAMSUNG"
(**) |   |-->Device "nVidia Corporation NV44 [GeForce 6200 LE]"
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
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 10de,02f1 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 0000,0000 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 10de,cb84 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 105b,0caf rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 105b,0caf rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 105b,0caf rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 105b,0caf rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 105b,0caf rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 105b,0caf rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 10de,cb84 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 10de,cb84 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:2: chip 10de,026b card 105b,0caf rev a2 class 04,01,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 105b,0caf rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 10de,0163 card 3842,c227 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:06:0: chip 104c,8023 card 105b,0caf rev 00 class 0c,00,10 hdr 00
(II) PCI: 04:07:0: chip 10b7,9055 card 10b7,9055 rev 30 class 02,00,00 hdr 00
(II) PCI: 04:08:0: chip 4444,0016 card 0070,8003 rev 01 class 04,00,00 hdr 00
(II) PCI: 04:09:0: chip 168c,0013 card 1385,5a00 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x00008000 - 0x000080ff (0x100) IX[B]
        [1] -1  0       0x00008400 - 0x000084ff (0x100) IX[B]
        [2] -1  0       0x00008800 - 0x000088ff (0x100) IX[B]
        [3] -1  0       0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [1] -1  0       0x0000a400 - 0x0000a4ff (0x100) IX[B]
        [2] -1  0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [3] -1  0       0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 3 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[B]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[B]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[B]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
        [0] -1  0       0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
        [0] -1  0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(3:0:0) nVidia Corporation NV44 [GeForce 6200 LE] rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(--) PCI: (4:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf4000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [1] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [2] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [3] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [4] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [5] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [6] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [7] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [8] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [9] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [10] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [13] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [15] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [16] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [19] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [20] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [21] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [22] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [23] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [24] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [25] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [26] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [27] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [28] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [29] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [30] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [1] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [2] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [3] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [4] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [5] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [6] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [7] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [8] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [9] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [10] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [11] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [12] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [13] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [15] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [16] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [18] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [19] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [20] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [21] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [22] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [23] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [24] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [25] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [26] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [27] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [28] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [29] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [30] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [20] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [21] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [23] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [24] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [25] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [26] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [27] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [28] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [29] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [30] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [31] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [32] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [33] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [34] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [35] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [36] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
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
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
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
        compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
        compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [20] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [21] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [23] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [24] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [25] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [26] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [27] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [28] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [29] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [30] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [31] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [32] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [33] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [34] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [35] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [36] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [5] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [6] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [7] -1  0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [8] -1  0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [9] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [10] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [11] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [12] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [13] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [14] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [24] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [25] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [26] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [27] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [28] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [29] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [30] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [31] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [32] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [33] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [34] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [35] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [36] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [37] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [38] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [39] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [40] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [41] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
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
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE (NV44) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 LE at PCI:3:0:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (37, 37); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfb000000 - 0xfbffffff (0x1000000) MX[B]
        [1] 0   0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
        [2] 0   0       0xfa000000 - 0xfaffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfdce0000 - 0xfdceffff (0x10000) MX[B]
        [8] -1  0       0xfdcfe000 - 0xfdcfe07f (0x80) MX[B]
        [9] -1  0       0xfdcf8000 - 0xfdcfbfff (0x4000) MX[B]
        [10] -1 0       0xfdcff000 - 0xfdcff7ff (0x800) MX[B]
        [11] -1 0       0xfe02a000 - 0xfe02afff (0x1000) MX[B]
        [12] -1 0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [13] -1 0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [14] -1 0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [15] -1 0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [16] -1 0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [17] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [18] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [19] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [20] -1 0       0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
        [21] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [22] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [23] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [25] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [26] -1 0       0x0000bc00 - 0x0000bc7f (0x80) IX[B]
        [27] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [29] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [30] -1 0       0x0000cc00 - 0x0000cc0f (0x10) IX[B]
        [31] -1 0       0x00000b60 - 0x00000b63 (0x4) IX[B]
        [32] -1 0       0x00000960 - 0x00000967 (0x8) IX[B]
        [33] -1 0       0x00000be0 - 0x00000be3 (0x4) IX[B]
        [34] -1 0       0x000009e0 - 0x000009e7 (0x8) IX[B]
        [35] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [36] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [37] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [38] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [39] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [40] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [41] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [42] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [43] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [44] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1920x1080"
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
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
$ 

```


And here is a copy of my /etc/X11/xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SAMSUNG"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44 [GeForce 6200 LE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44 [GeForce 6200 LE]"
    Monitor        "SAMSUNG"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

$ 

```

As for the system, it's an Acer AMD Athlon64 that I bought in the spring of '06 (so I wouldn't call it bleeding edge) running the -386 Fiesty kernel (I had the same problem with the -generic kernel).  The only funny thing about the system is that the monitor is actually a 1080p TV.  However, I have the same problems when hooked up to a regular LCD monitor as well.


Any help whatsoever is appreciated.

---

### Post by dabl on 2007-07-05
Well, congratulations on ten great minutes! :twisted:

The GeF 6200 LE is supported with the new Nvidia driver, according to their site, so it should be the right choice for a driver.

OK, do you actually need the wacom, aka tablet PC features?  If not, you can safely comment out the 3 lines in the "Server Layout" stanza of xorg.conf that contain the words "stylus", "cursor", and "eraser", and then also comment out the entire stanzas for each of those, i.e. these three:

> Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

( I assume you understand that when I say "comment out" I mean edit the file and place a "#" at the beginning of each line to be excluded.)

Now, the errors regarding X11/fonts and X11/cyrillic are vaguely familiar -- I've seen them before (but not on my system). I'm not sure whether I saw posts on this forum or Kubuntu Forum, but there have been posts regarding these errors.  I recommend you search on those terms, and see if you can learn what the remedy was.

Neither the wacom driver issues nor the X11/fonts problems seem to me to be capable of locking your X server, but then it won't hurt to clear them up, either.  Also, I seriously doubt that the HDTV is a source of trouble, but if you could connect to a real monitor for 20 minutes, you could probably prove it.    :)

---

### Post by mmcmonster on 2007-07-06
Same problem happened yet again.  I have another nvidia 6200 card in another system, and it works fine (good resolution and no fan, so the system keeps quiet).

Here is the current /etc/X11/xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "SAMSUNG"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44 [GeForce 6200 LE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44 [GeForce 6200 LE]"
    Monitor        "SAMSUNG"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by mmcmonster on 2007-07-06
I'm not sure if this is of help, but here is my /var/log/kern.log:
```

Jul  6 18:41:17 mythtv kernel: [   45.077663] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
Jul  6 18:41:17 mythtv kernel: [   45.077679] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Jul  6 18:41:17 mythtv kernel: [   45.077684] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Jul  6 18:41:17 mythtv kernel: [   45.077840] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Jul  6 18:41:17 mythtv kernel: [   45.077881] ehci_hcd 0000:00:0b.1: debug port 1
Jul  6 18:41:17 mythtv kernel: [   45.077887] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Jul  6 18:41:17 mythtv kernel: [   45.077901] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfe02e000
Jul  6 18:41:17 mythtv kernel: [   45.077912] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  6 18:41:17 mythtv kernel: [   45.078022] usb usb1: configuration #1 chosen from 1 choice
Jul  6 18:41:17 mythtv kernel: [   45.078054] hub 1-0:1.0: USB hub found
Jul  6 18:41:17 mythtv kernel: [   45.078065] hub 1-0:1.0: 8 ports detected
Jul  6 18:41:17 mythtv kernel: [   45.125913] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
Jul  6 18:41:17 mythtv kernel: [   45.161909] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  6 18:41:17 mythtv kernel: [   45.211511] ieee1394: Initialized config rom entry `ip1394'
Jul  6 18:41:17 mythtv kernel: [   45.213972] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jul  6 18:41:17 mythtv kernel: [   45.213987] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 17
Jul  6 18:41:17 mythtv kernel: [   45.317902] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jul  6 18:41:17 mythtv kernel: [   45.342978] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
Jul  6 18:41:17 mythtv kernel: [   45.343005] NFORCE-MCP51: chipset revision 161
Jul  6 18:41:17 mythtv kernel: [   45.343009] NFORCE-MCP51: not 100%% native mode: will probe irqs later
Jul  6 18:41:17 mythtv kernel: [   45.343020] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
Jul  6 18:41:17 mythtv kernel: [   45.343031]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
Jul  6 18:41:17 mythtv kernel: [   45.343046]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
Jul  6 18:41:17 mythtv kernel: [   45.343056] Probing IDE interface ide0...
Jul  6 18:41:17 mythtv kernel: [   45.360888] SCSI subsystem initialized
Jul  6 18:41:17 mythtv kernel: [   45.368440] libata version 2.20 loaded.
Jul  6 18:41:17 mythtv kernel: [   45.606102] FDC 0 is a post-1991 82077
Jul  6 18:41:17 mythtv kernel: [   45.621686] usb 1-6: new high speed USB device using ehci_hcd and address 3
Jul  6 18:41:17 mythtv kernel: [   45.843882] usb 1-6: configuration #1 chosen from 1 choice
Jul  6 18:41:17 mythtv kernel: [   45.909597] Probing IDE interface ide1...
Jul  6 18:41:17 mythtv kernel: [   46.029615] usbcore: registered new interface driver libusual
Jul  6 18:41:17 mythtv kernel: [   46.036355] Initializing USB Mass Storage driver...
Jul  6 18:41:17 mythtv kernel: [   46.036456] scsi0 : SCSI emulation for USB Mass Storage devices
Jul  6 18:41:17 mythtv kernel: [   46.036510] usb-storage: device found at 3
Jul  6 18:41:17 mythtv kernel: [   46.036513] usb-storage: waiting for device to settle before scanning
Jul  6 18:41:17 mythtv kernel: [   46.036524] usbcore: registered new interface driver usb-storage
Jul  6 18:41:17 mythtv kernel: [   46.036528] USB Mass Storage support registered.
Jul  6 18:41:17 mythtv kernel: [   46.589530] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200012ce13]
Jul  6 18:41:17 mythtv kernel: [   46.645497] hdc: HL-DT-STDVDRRW GWA-4164B, ATAPI CD/DVD-ROM drive
Jul  6 18:41:17 mythtv kernel: [   47.429274] hdd: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
Jul  6 18:41:17 mythtv kernel: [   47.486646] ide1 at 0x170-0x177,0x376 on irq 15
Jul  6 18:41:17 mythtv kernel: [   47.493946] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Jul  6 18:41:17 mythtv kernel: [   47.493961] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 18
Jul  6 18:41:17 mythtv kernel: [   47.493970] PCI: Setting latency timer of device 0000:00:14.0 to 64
Jul  6 18:41:17 mythtv kernel: [   47.493981] forcedeth: using HIGHDMA
Jul  6 18:41:17 mythtv kernel: [   48.013449] eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
Jul  6 18:41:17 mythtv kernel: [   48.014344] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Jul  6 18:41:17 mythtv kernel: [   48.014357] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 19
Jul  6 18:41:17 mythtv kernel: [   48.014372] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Jul  6 18:41:17 mythtv kernel: [   48.014377] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Jul  6 18:41:17 mythtv kernel: [   48.014537] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Jul  6 18:41:17 mythtv kernel: [   48.014561] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xfe02f000
Jul  6 18:41:17 mythtv kernel: [   48.072355] usb usb2: configuration #1 chosen from 1 choice
Jul  6 18:41:17 mythtv kernel: [   48.072530] hub 2-0:1.0: USB hub found
Jul  6 18:41:17 mythtv kernel: [   48.072548] hub 2-0:1.0: 8 ports detected
Jul  6 18:41:17 mythtv kernel: [   48.178825] sata_nv 0000:00:0e.0: version 3.3
Jul  6 18:41:17 mythtv kernel: [   48.179621] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Jul  6 18:41:17 mythtv kernel: [   48.179635] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
Jul  6 18:41:17 mythtv kernel: [   48.179660] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Jul  6 18:41:17 mythtv kernel: [   48.179715] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 20
Jul  6 18:41:17 mythtv kernel: [   48.179743] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 20
Jul  6 18:41:17 mythtv kernel: [   48.179764] scsi1 : sata_nv
Jul  6 18:41:17 mythtv kernel: [   48.476880] usb 2-5: new low speed USB device using ohci_hcd and address 2
Jul  6 18:41:17 mythtv kernel: [   48.644855] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  6 18:41:17 mythtv kernel: [   48.653110] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Jul  6 18:41:17 mythtv kernel: [   48.653118] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
Jul  6 18:41:17 mythtv kernel: [   48.653123] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  6 18:41:17 mythtv kernel: [   48.661094] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
Jul  6 18:41:17 mythtv kernel: [   48.661101] ata1.00: configured for UDMA/133
Jul  6 18:41:17 mythtv kernel: [   48.661111] scsi2 : sata_nv
Jul  6 18:41:17 mythtv kernel: [   48.691873] usb 2-5: configuration #1 chosen from 1 choice
Jul  6 18:41:17 mythtv kernel: [   48.972745] ata2: SATA link down (SStatus 0 SControl 300)
Jul  6 18:41:17 mythtv kernel: [   48.983295] ATA: abnormal status 0x7F on port 0x00010977
Jul  6 18:41:17 mythtv kernel: [   48.983433] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
Jul  6 18:41:17 mythtv kernel: [   48.985474] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Jul  6 18:41:17 mythtv kernel: [   48.985479] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Jul  6 18:41:17 mythtv kernel: [   48.985511] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Jul  6 18:41:17 mythtv kernel: [   48.985551] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 16
Jul  6 18:41:17 mythtv kernel: [   48.985579] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 16
Jul  6 18:41:17 mythtv kernel: [   48.985592] scsi3 : sata_nv
Jul  6 18:41:17 mythtv kernel: [   49.000738] usb 2-8: new low speed USB device using ohci_hcd and address 3
Jul  6 18:41:17 mythtv kernel: [   49.214706] usb 2-8: configuration #1 chosen from 1 choice
Jul  6 18:41:17 mythtv kernel: [   49.219677] usbcore: registered new interface driver hiddev
Jul  6 18:41:17 mythtv kernel: [   49.233792] input: Acer MCE Receiver as /class/input/input1
Jul  6 18:41:17 mythtv kernel: [   49.233837] input,hiddev96: USB HID v1.10 Keyboard [Acer MCE Receiver] on usb-0000:00:0b.0-5
Jul  6 18:41:17 mythtv kernel: [   49.238779] input: Logitech USB Receiver as /class/input/input2
Jul  6 18:41:17 mythtv kernel: [   49.238797] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-8
Jul  6 18:41:17 mythtv kernel: [   49.248854] input: Logitech USB Receiver as /class/input/input3
Jul  6 18:41:17 mythtv kernel: [   49.248914] input,hiddev97: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-8
Jul  6 18:41:17 mythtv kernel: [   49.248933] usbcore: registered new interface driver usbhid
Jul  6 18:41:17 mythtv kernel: [   49.248939] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jul  6 18:41:17 mythtv kernel: [   49.452636] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  6 18:41:17 mythtv kernel: [   49.461791] ata3.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
Jul  6 18:41:17 mythtv kernel: [   49.461800] ata3.00: ATA-7: Maxtor 6V250F0, VA111630, max UDMA/133
Jul  6 18:41:17 mythtv kernel: [   49.461805] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  6 18:41:17 mythtv kernel: [   49.469781] ata3.00: ata_hpa_resize 1: sectors = 490234752, hpa_sectors = 490234752
Jul  6 18:41:17 mythtv kernel: [   49.469787] ata3.00: configured for UDMA/133
Jul  6 18:41:17 mythtv kernel: [   49.469798] scsi4 : sata_nv
Jul  6 18:41:17 mythtv kernel: [   49.780520] ata4: SATA link down (SStatus 0 SControl 300)
Jul  6 18:41:17 mythtv kernel: [   49.791067] ATA: abnormal status 0x7F on port 0x00010967
Jul  6 18:41:17 mythtv kernel: [   49.791196] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6V250F0   VA11 PQ: 0 ANSI: 5
Jul  6 18:41:17 mythtv kernel: [   49.793648] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Jul  6 18:41:17 mythtv kernel: [   49.793663] ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
Jul  6 18:41:17 mythtv kernel: [   49.793673] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
Jul  6 18:41:17 mythtv kernel: [   49.793681] 0000:04:07.0: 3Com PCI 3c905B Cyclone 100baseTx at f8838000.
Jul  6 18:41:17 mythtv kernel: [   49.847216] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Jul  6 18:41:17 mythtv kernel: [   49.847228] Uniform CD-ROM driver Revision: 3.20
Jul  6 18:41:17 mythtv kernel: [   49.847687] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Jul  6 18:41:17 mythtv kernel: [   49.848026] sda: Write Protect is off
Jul  6 18:41:17 mythtv kernel: [   49.848031] sda: Mode Sense: 00 3a 00 00
Jul  6 18:41:17 mythtv kernel: [   49.848526] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 18:41:17 mythtv kernel: [   49.848998] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Jul  6 18:41:17 mythtv kernel: [   49.849013] sda: Write Protect is off
Jul  6 18:41:17 mythtv kernel: [   49.849016] sda: Mode Sense: 00 3a 00 00
Jul  6 18:41:17 mythtv kernel: [   49.849033] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 18:41:17 mythtv kernel: [   49.849038]  sda:<6>hdd: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
Jul  6 18:41:17 mythtv kernel: [   49.881427]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Jul  6 18:41:17 mythtv kernel: [   49.938417] sd 1:0:0:0: Attached scsi disk sda
Jul  6 18:41:17 mythtv kernel: [   49.938625] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
Jul  6 18:41:17 mythtv kernel: [   49.938640] sdb: Write Protect is off
Jul  6 18:41:17 mythtv kernel: [   49.938644] sdb: Mode Sense: 00 3a 00 00
Jul  6 18:41:17 mythtv kernel: [   49.938662] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 18:41:17 mythtv kernel: [   49.938717] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
Jul  6 18:41:17 mythtv kernel: [   49.938727] sdb: Write Protect is off
Jul  6 18:41:17 mythtv kernel: [   49.938731] sdb: Mode Sense: 00 3a 00 00
Jul  6 18:41:17 mythtv kernel: [   49.938747] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 18:41:17 mythtv kernel: [   49.938753]  sdb: sdb1 < sdb5 >
Jul  6 18:41:17 mythtv kernel: [   49.960325] sd 3:0:0:0: Attached scsi disk sdb
Jul  6 18:41:17 mythtv kernel: [   49.967396] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jul  6 18:41:17 mythtv kernel: [   49.967562] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jul  6 18:41:17 mythtv kernel: [   50.239319] Attempting manual resume
Jul  6 18:41:17 mythtv kernel: [   50.239325] swsusp: Resume From Partition 8:6
Jul  6 18:41:17 mythtv kernel: [   50.239328] PM: Checking swsusp image.
Jul  6 18:41:17 mythtv kernel: [   50.239538] PM: Resume from disk failed.
Jul  6 18:41:17 mythtv kernel: [   50.279450] kjournald starting.  Commit interval 5 seconds
Jul  6 18:41:17 mythtv kernel: [   50.279463] EXT3-fs: mounted filesystem with ordered data mode.
Jul  6 18:41:17 mythtv kernel: [   51.040339] usb-storage: device scan complete
Jul  6 18:41:17 mythtv kernel: [   51.071455] scsi 0:0:0:0: Direct-Access     Generic  2.0 Reader-CF    1.00 PQ: 0 ANSI: 0 CCS
Jul  6 18:41:17 mythtv kernel: [   51.102438] scsi 0:0:0:1: Direct-Access     Generic  2.0 Reader-SM/xD 1.00 PQ: 0 ANSI: 0 CCS
Jul  6 18:41:17 mythtv kernel: [   51.133428] scsi 0:0:0:2: Direct-Access     Generic  2.0 Reader-SD    1.00 PQ: 0 ANSI: 0 CCS
Jul  6 18:41:17 mythtv kernel: [   51.164417] scsi 0:0:0:3: Direct-Access     Generic  2.0 Reader-MS    1.00 PQ: 0 ANSI: 0 CCS
Jul  6 18:41:17 mythtv kernel: [   51.166444] sd 0:0:0:0: Attached scsi removable disk sdc
Jul  6 18:41:17 mythtv kernel: [   51.166485] sd 0:0:0:0: Attached scsi generic sg2 type 0
Jul  6 18:41:17 mythtv kernel: [   51.168436] sd 0:0:0:1: Attached scsi removable disk sdd
Jul  6 18:41:17 mythtv kernel: [   51.168474] sd 0:0:0:1: Attached scsi generic sg3 type 0
Jul  6 18:41:17 mythtv kernel: [   51.170435] sd 0:0:0:2: Attached scsi removable disk sde
Jul  6 18:41:17 mythtv kernel: [   51.170474] sd 0:0:0:2: Attached scsi generic sg4 type 0
Jul  6 18:41:17 mythtv kernel: [   51.172429] sd 0:0:0:3: Attached scsi removable disk sdf
Jul  6 18:41:17 mythtv kernel: [   51.172469] sd 0:0:0:3: Attached scsi generic sg5 type 0
Jul  6 18:41:17 mythtv kernel: [   57.334546] eth1:  setting half-duplex.
Jul  6 18:41:17 mythtv kernel: [   57.690066] eth0: no link during initialization.
Jul  6 18:41:17 mythtv kernel: [   59.000492] NET: Registered protocol family 17
Jul  6 18:41:17 mythtv kernel: [   60.252088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  6 18:41:17 mythtv kernel: [   60.273963] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  6 18:41:17 mythtv kernel: [   61.106326] ath_hal: module license 'Proprietary' taints kernel.
Jul  6 18:41:17 mythtv kernel: [   61.107238] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul  6 18:41:17 mythtv kernel: [   61.300404] Linux video capture interface: v2.00
Jul  6 18:41:17 mythtv kernel: [   61.369750] ivtv:  ==================== START INIT IVTV ====================
Jul  6 18:41:17 mythtv kernel: [   61.369757] ivtv:  version 0.10.1 (tagged release) loading
Jul  6 18:41:17 mythtv kernel: [   61.369760] ivtv:  Linux version: 2.6.20-16-386 mod_unload 486 
Jul  6 18:41:17 mythtv kernel: [   61.369764] ivtv:  In case of problems please include the debug info between
Jul  6 18:41:17 mythtv kernel: [   61.369768] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Jul  6 18:41:17 mythtv kernel: [   61.369772] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Jul  6 18:41:17 mythtv kernel: [   61.369870] ivtv0: Autodetected Hauppauge card (cx23416 based)
Jul  6 18:41:17 mythtv kernel: [   61.370741] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Jul  6 18:41:17 mythtv kernel: [   61.370756] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
Jul  6 18:41:17 mythtv kernel: [   61.370771] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Jul  6 18:41:17 mythtv kernel: [   61.596811] Linux agpgart interface v0.102 (c) Dave Jones
Jul  6 18:41:17 mythtv kernel: [   61.814216] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Jul  6 18:41:17 mythtv kernel: [   61.814258] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
Jul  6 18:41:17 mythtv kernel: [   61.976785] wlan: 0.8.4.2 (0.9.3.1)
Jul  6 18:41:17 mythtv kernel: [   62.587465] Real Time Clock Driver v1.12ac
Jul  6 18:41:17 mythtv kernel: [   62.625272] ath_pci: 0.9.4.5 (0.9.3.1)
Jul  6 18:41:17 mythtv kernel: [   62.677447] input: PC Speaker as /class/input/input4
Jul  6 18:41:17 mythtv kernel: [   62.736170] parport: PnPBIOS parport detected.
Jul  6 18:41:17 mythtv kernel: [   62.736230] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul  6 18:41:17 mythtv kernel: [   62.750040] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Jul  6 18:41:17 mythtv kernel: [   62.758239] irda_init()
Jul  6 18:41:17 mythtv kernel: [   62.758267] NET: Registered protocol family 23
Jul  6 18:41:17 mythtv kernel: [   62.966196] ivtv0: Encoder revision: 0x02050032
Jul  6 18:41:17 mythtv kernel: [   62.966202] ivtv0: Recommended firmware version is 0x02060039.
Jul  6 18:41:17 mythtv kernel: [   63.036509] tveeprom 2-0050: Hauppauge model 26132, rev F1B2, serial# 9898635
Jul  6 18:41:17 mythtv kernel: [   63.036517] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
Jul  6 18:41:17 mythtv kernel: [   63.036522] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
Jul  6 18:41:17 mythtv kernel: [   63.036527] tveeprom 2-0050: audio processor is CX25841 (idx 35)
Jul  6 18:41:17 mythtv kernel: [   63.036531] tveeprom 2-0050: decoder processor is CX25841 (idx 28)
Jul  6 18:41:17 mythtv kernel: [   63.036535] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
Jul  6 18:41:17 mythtv kernel: [   63.036540] ivtv0: Autodetected Hauppauge WinTV PVR-150
Jul  6 18:41:17 mythtv kernel: [   63.036544] ivtv0: reopen i2c bus for IR-blaster support
Jul  6 18:41:17 mythtv kernel: [   63.168971] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Jul  6 18:41:17 mythtv kernel: [   63.916435] cx25840 2-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
Jul  6 18:41:17 mythtv kernel: [   67.821492] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Jul  6 18:41:17 mythtv kernel: [   67.940027] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
Jul  6 18:41:17 mythtv kernel: [   67.989816] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Jul  6 18:41:17 mythtv kernel: [   67.990208] ivtv0: Registered device video32 for encoder YUV (2 MB)
Jul  6 18:41:17 mythtv kernel: [   67.990586] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Jul  6 18:41:17 mythtv kernel: [   67.990840] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Jul  6 18:41:17 mythtv kernel: [   67.991081] tuner 2-0061: type set to 50 (TCL 2002N)
Jul  6 18:41:17 mythtv kernel: [   68.333354] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Jul  6 18:41:17 mythtv kernel: [   68.333374] ivtv:  ====================  END INIT IVTV  ====================
Jul  6 18:41:17 mythtv kernel: [   68.336890] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jul  6 18:41:17 mythtv kernel: [   68.336907] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 23
Jul  6 18:41:17 mythtv kernel: [   68.942644] ath_rate_sample: 1.2 (0.9.3.1)
Jul  6 18:41:17 mythtv kernel: [   68.943004] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul  6 18:41:17 mythtv kernel: [   68.943013] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  6 18:41:17 mythtv kernel: [   68.943026] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  6 18:41:17 mythtv kernel: [   68.943035] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul  6 18:41:17 mythtv kernel: [   68.943041] wifi0: mac 7.9 phy 4.5 radio 5.6
Jul  6 18:41:17 mythtv kernel: [   68.943047] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul  6 18:41:17 mythtv kernel: [   68.943051] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul  6 18:41:17 mythtv kernel: [   68.943054] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul  6 18:41:17 mythtv kernel: [   68.943058] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul  6 18:41:17 mythtv kernel: [   68.943061] wifi0: Use hw queue 8 for CAB traffic
Jul  6 18:41:17 mythtv kernel: [   68.943064] wifi0: Use hw queue 9 for beacons
Jul  6 18:41:17 mythtv kernel: [   68.960292] wifi0: Atheros 5212: mem=0xfdce0000, irq=23
Jul  6 18:41:17 mythtv kernel: [   68.961858] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Jul  6 18:41:17 mythtv kernel: [   68.961865] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 18
Jul  6 18:41:17 mythtv kernel: [   68.961895] PCI: Setting latency timer of device 0000:00:10.2 to 64
Jul  6 18:41:17 mythtv kernel: [   69.279168] intel8x0_measure_ac97_clock: measured 54637 usecs
Jul  6 18:41:17 mythtv kernel: [   69.279174] intel8x0: clocking to 46971
Jul  6 18:41:17 mythtv kernel: [   69.480243] fuse init (API version 7.8)
Jul  6 18:41:17 mythtv kernel: [   69.505654] lp0: using parport0 (interrupt-driven).
Jul  6 18:41:17 mythtv kernel: [   69.578144] Adding 1020088k swap on /dev/disk/by-uuid/0a7e2ebb-2f1e-4730-90a3-12fb6d18f359.  Priority:-1 extents:1 across:1020088k
Jul  6 18:41:17 mythtv kernel: [   69.771976] EXT3 FS on sda5, internal journal
Jul  6 18:41:17 mythtv kernel: [   70.997024] kjournald starting.  Commit interval 5 seconds
Jul  6 18:41:17 mythtv kernel: [   70.997302] EXT3 FS on sda7, internal journal
Jul  6 18:41:17 mythtv kernel: [   70.997308] EXT3-fs: mounted filesystem with ordered data mode.
Jul  6 18:41:17 mythtv kernel: [   71.038420] kjournald starting.  Commit interval 5 seconds
Jul  6 18:41:17 mythtv kernel: [   71.039486] EXT3 FS on sdb5, internal journal
Jul  6 18:41:17 mythtv kernel: [   71.039492] EXT3-fs: mounted filesystem with ordered data mode.
Jul  6 18:41:17 mythtv kernel: [   71.248035] NTFS driver 2.1.28 [Flags: R/O MODULE].
Jul  6 18:41:17 mythtv kernel: [   71.318304] NTFS volume version 3.1.
Jul  6 18:41:17 mythtv kernel: [   74.614519] ibm_acpi: ec object not found
Jul  6 18:41:17 mythtv kernel: [   74.701200] input: Power Button (FF) as /class/input/input5
Jul  6 18:41:17 mythtv kernel: [   74.708091] ACPI: Power Button (FF) [PWRF]
Jul  6 18:41:17 mythtv kernel: [   74.759728] input: Power Button (CM) as /class/input/input6
Jul  6 18:41:17 mythtv kernel: [   74.766538] ACPI: Power Button (CM) [PWRB]
Jul  6 18:41:17 mythtv kernel: [   75.285220] Using specific hotkey driver
Jul  6 18:41:17 mythtv kernel: [   75.387129] No dock devices found.
Jul  6 18:41:17 mythtv kernel: [   75.436874] pcc_acpi: loading...
Jul  6 18:41:17 mythtv kernel: [   75.678820] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
Jul  6 18:41:17 mythtv kernel: [   75.678874] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
Jul  6 18:41:17 mythtv kernel: [   75.678879] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
Jul  6 18:41:17 mythtv kernel: [   75.678884] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
Jul  6 18:41:17 mythtv kernel: [   75.678888] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jul  6 18:41:17 mythtv kernel: [   43.708000] Time: acpi_pm clocksource has been installed.
Jul  6 18:41:19 mythtv kernel: [   45.316000] NET: Registered protocol family 10
Jul  6 18:41:19 mythtv kernel: [   45.316000] lo: Disabled Privacy Extensions
Jul  6 18:41:19 mythtv kernel: [   45.316000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  6 18:41:19 mythtv kernel: [   45.316000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  6 18:41:19 mythtv kernel: [   45.316000] ADDRCONF(NETDEV_UP): ath0: link is not ready
Jul  6 18:41:20 mythtv kernel: [   46.856000] ppdev: user-space parallel port driver
Jul  6 18:41:21 mythtv kernel: [   47.472000] lirc_dev: IR Remote Control driver registered, at major 61 
Jul  6 18:41:21 mythtv kernel: [   47.476000] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
Jul  6 18:41:21 mythtv kernel: [   47.512000] lirc_pvr150: chip found with RX and TX
Jul  6 18:41:21 mythtv kernel: [   47.512000] lirc_dev: lirc_register_plugin: sample_rate: 0
Jul  6 18:41:21 mythtv kernel: [   47.520000] lirc_pvr150: firmware haup-ir-blaster.bin not available (-2)
Jul  6 18:41:21 mythtv kernel: [   47.572000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul  6 18:41:21 mythtv kernel: [   47.572000] apm: overridden by ACPI.
Jul  6 18:41:22 mythtv kernel: [   48.736000] Bluetooth: Core ver 2.11
Jul  6 18:41:22 mythtv kernel: [   48.736000] NET: Registered protocol family 31
Jul  6 18:41:22 mythtv kernel: [   48.736000] Bluetooth: HCI device and connection manager initialized
Jul  6 18:41:22 mythtv kernel: [   48.736000] Bluetooth: HCI socket layer initialized
Jul  6 18:41:22 mythtv kernel: [   48.784000] Bluetooth: L2CAP ver 2.8
Jul  6 18:41:22 mythtv kernel: [   48.784000] Bluetooth: L2CAP socket layer initialized
Jul  6 18:41:22 mythtv kernel: [   48.792000] Bluetooth: RFCOMM socket layer initialized
Jul  6 18:41:22 mythtv kernel: [   48.792000] Bluetooth: RFCOMM TTY layer initialized
Jul  6 18:41:22 mythtv kernel: [   48.792000] Bluetooth: RFCOMM ver 1.8
Jul  6 18:41:30 mythtv kernel: [   56.812000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Jul  6 18:41:40 mythtv kernel: [   72.104000] ath0: no IPv6 routers present
Jul  6 21:20:12 mythtv kernel: [ 9583.252000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Jul  6 21:20:12 mythtv kernel: [ 9583.252000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
Jul  6 21:20:12 mythtv kernel: [ 9583.252000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Jul  6 21:20:12 mythtv kernel: [ 9583.252000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
Jul  6 21:24:16 mythtv kernel: [ 9827.296000] NVRM: Xid (0003:00): 16, Head 00000000 Count 00006d80
Jul  6 21:24:19 mythtv kernel: [ 9830.296000] NVRM: Xid (0003:00): 8, Channel 00000000
Jul  6 21:24:34 mythtv kernel: [ 9845.296000] NVRM: Xid (0003:00): 16, Head 00000000 Count 00006f62
Jul  6 21:24:35 mythtv kernel: [ 9846.296000] NVRM: Xid (0003:00): 8, Channel 0000001e
Jul  6 21:24:42 mythtv kernel: [ 9853.296000] NVRM: Xid (0003:00): 16, Head 00000000 Count 00006f63
Jul  6 21:24:43 mythtv kernel: [ 9854.296000] NVRM: Xid (0003:00): 8, Channel 00000020
Jul  6 21:24:50 mythtv kernel: [ 9861.296000] NVRM: Xid (0003:00): 16, Head 00000000 Count 00006f64
Jul  6 21:24:51 mythtv kernel: [ 9862.296000] NVRM: Xid (0003:00): 8, Channel 00000020

```

---

### Post by dabl on 2007-07-06
Geez, I don't see anything wrong with your xorg.conf file.

Is it possible there's a hardware problem, such as a thermal-induced electrical "open" (cold solder joint)?  It's odd that it seems to fail after heating up.

Would it possible to swap the GeF 6200 cards, to test the possibility of a hardware issue?  I know it's a pain ....

---

### Post by mmcmonster on 2007-07-07
Actually, I never thought of that.  I'll give it a try (swapping the cards) this weekend.

---

### Post by mmcmonster on 2007-07-07
&@^%$  The two nvidia 6200 cards have different connections (the system that is giving me problems has a PCI-e connector, I believe).

As another piece of information: The system had no problems running Windows XP with nvidia drivers, and runs ubuntu fine (no hanging in X) if I use the default 'nv' drivers.  It's when I run nvidia drivers under linux that I have a problem.

Any other ideas. :-(

---

### Post by The last Bert on 2007-07-07
I too have a GeForce 6200, and can't get it working. It works fine with the nv drivers, but after the nvidia drivers have been installed, X seems to crash on startup. I've tried a couple of different ways of installing the drivers now, and still got nothing. Is this a problem with the 6200?

---

### Post by mmcmonster on 2007-07-08
As I mentioned, I have another GF6200 that works perfectly fine with nvidia drivers (I even play with compiz occasionally).

Maybe an issue with GF6200 which use the PCI-e connector?

---

