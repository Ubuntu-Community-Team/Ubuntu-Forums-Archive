---
title: "3d-acceleration wont work on Radeon 9800XT"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by n1ppon on 2007-10-24
Hi, I've been trying with the new function which came along with Gusty(Restricted Drivers) and I've been trying with Envy-script. Im quite new with linux and I tried to get some help from #Ubuntu-se@freenode and the came up with the answer that there was something wrong with DRI, and told me to ask at #Xorg@freenode. At xorg they told me that there was something wrong with the "agp-bridge" and they didnt know how to solve it in Ubuntu. Then I turned to #Ubuntu@Q-net and told them everything that had been said in the earlier channels and then they gave me a link and said: "This looks like your problem" (The link: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)). But as Im new to this I dont really know what to do. Im running with intel P4 3.2 ghz and radeon 9800XT(agp)

Please help, here's some random information that might be helpful. Thanks.


Xorg.0.log:
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux alpha 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 12:16:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Allmän skärm"
(**) |   |-->Device "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "AIGLX" "off"
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 8086,2578 card 147b,1021 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,257b card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 8086,257e card 147b,1021 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 147b,1021 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 147b,1021 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 147b,1021 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 147b,1021 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 147b,1021 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,24d1 card 147b,1021 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 147b,1021 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 147b,1021 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e4a card 1043,c000 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e6a card 1043,c001 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1019 card 147b,1021 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:02:0: chip 104c,8024 card 147b,1021 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:03:0: chip 1095,3114 card 1095,6114 rev 02 class 01,04,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf40fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
	[4] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[5] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[6] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[7] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 NJ [Radeon 9800 XT] rev 0, Mem @ 0xe0000000/27, 0xf1000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary) rev 0, Mem @ 0xe8000000/27, 0xf1010000/16
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[1] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[2] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[3] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[4] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[5] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[6] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[7] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[12] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[13] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[14] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[15] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[16] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[1] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[2] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[3] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[4] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[5] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[6] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[7] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[12] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[13] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[14] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[15] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[16] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[5] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[6] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[7] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[8] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[9] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[10] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[11] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[20] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[21] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[22] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[23] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.40.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.40.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.402                    
(II) ATI Proprietary Linux Driver Build Date: Jul 31 2007 22:20:14
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E4A) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[5] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[6] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[7] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[8] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[9] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[10] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[11] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[20] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[21] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[22] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[23] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208d60
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[5] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[6] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[7] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[8] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[9] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[10] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[11] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[23] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[24] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[25] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[26] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[27] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[38] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[40] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 XT" (Chipset = 0x4e4a)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0xc000)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI R360
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R360
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
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
	compiled for 7.1.0, module version = 8.40.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 1dd  Serial#: 1212231991
(II) fglrx(0): Year: 2006  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HVEA101432
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2ddd0137314148
(II) fglrx(0): 	0110010380221b782aaaa5a654549926
(II) fglrx(0): 	145054bfef8081808140714f01010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000fd00384b1e
(II) fglrx(0): 	510e000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	00485645413130313433320a202000df
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 53 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1280x1024@75": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864@75": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864@75"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0): *Mode "1280x1024@60": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1024x768@60": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@60"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@60": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@60"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0):  Default mode "1024x768@60": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@70"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@70": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@70"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0):  Default mode "1024x768@70": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@75": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@75"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@75": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@75"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0): *Mode "1024x768@75": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "832x624@75": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "832x624@75"   57.28  832 864 928 1152  624 625 628 667 interlace +vsync
(**) fglrx(0): *Mode "800x600@60": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@60": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@75": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@72": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@75": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@72": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
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
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (119, 112)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1280x1024@75": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@75": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@75"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864@75": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864@75"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0): *Mode "1280x1024@60": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x1024@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024@60"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1024x768@60": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@60"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@60": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@60"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0):  Default mode "1024x768@60": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@60"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@70": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@70"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@70": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@70"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0):  Default mode "1024x768@70": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@70"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x768@75": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768@75"   78.80  1024 1040 1136 1312  768 769 772 800 doublescan +hsync
(**) fglrx(0): *Mode "1024x768@75": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz (I)
(II) fglrx(0): Modeline "1024x768@75"   75.00  1024 1048 1184 1328  768 771 777 806 interlace +vsync
(**) fglrx(0): *Mode "1024x768@75": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768@75"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "832x624@75": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.0 Hz (I)
(II) fglrx(0): Modeline "832x624@75"   57.28  832 864 928 1152  624 625 628 667 interlace +vsync
(**) fglrx(0): *Mode "800x600@60": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@60": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@60": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@60"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@75": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@75": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@75"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@72": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0):  Default mode "800x600@72": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@72"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   49.50  800 816 896 1056  600 601 604 625 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   50.00  800 856 976 1040  600 637 643 666 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   40.00  800 840 968 1056  600 601 605 628 doublescan +hsync
(**) fglrx(0): *Mode "800x600@56": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz (D)
(II) fglrx(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 doublescan +hsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@75": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@75": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@75"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@72": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0):  Default mode "640x480@72": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@72"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 656 720 840  480 481 484 500 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   31.50  640 664 704 832  480 489 491 520 interlace +vsync
(**) fglrx(0): *Mode "640x480@60": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (I)
(II) fglrx(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 interlace +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
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
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
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
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf1000000 - 0xf100ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf3004000 - 0xf30043ff (0x400) MX[B]
	[7] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B]
	[8] -1	0	0xf3005000 - 0xf30057ff (0x800) MX[B]
	[9] -1	0	0xf4000000 - 0xf401ffff (0x20000) MX[B]
	[10] -1	0	0xf4103000 - 0xf41030ff (0x100) MX[B]
	[11] -1	0	0xf4102000 - 0xf41021ff (0x200) MX[B]
	[12] -1	0	0xf4100000 - 0xf41003ff (0x400) MX[B]
	[13] -1	0	0xf4101000 - 0xf4101fff (0x1000) MX[B]
	[14] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[15] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[18] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008000 - 0x0000800f (0x10) IX[B]
	[26] -1	0	0x00007c00 - 0x00007c03 (0x4) IX[B]
	[27] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[28] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[29] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[30] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[40] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[41] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[42] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
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
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7b79000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.40.4
(II) fglrx(0):     Date: Jul 31 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [pci] find AGP GART
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7b79000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 6991
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
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
(WW) fglrx(0): Option "MergedFB" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
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
	compiled for 1.3.0, module version = 1.0.0
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
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
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
```

glxinfo |grep direct : 
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

lsmod |grep dri: *Nothing*

lsmod |grep fglrx :
```
fglrx                 738976  3 
agpgart                35016  2 fglrx,intel_agp
```

lsmod |grep intel_agp :
```
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp

```

lsmod |grep agpgart :
```
agpgart                35016  2 fglrx,intel_agp
```

---

