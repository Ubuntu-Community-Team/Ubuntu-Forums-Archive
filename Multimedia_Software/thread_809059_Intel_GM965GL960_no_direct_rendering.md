---
title: "Intel GM965/GL960 no direct rendering"
date: 2008-05-27
forum: Multimedia Software
---

### Post by jamesattard on 2008-05-27
I think I noticed my problem when I did upgrade my xorg/kernel. This is my output:

> james@itsd01947:~$ lspci | grep -i gm
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)



> james@itsd01947:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

> james@itsd01947:~$ uname -a
Linux itsd01947 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

Xorg.log:

> This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux itsd01947 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 27 09:33:06 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 1462,401b rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a02 card 1462,401b rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a03 card 1462,401b rev 03 class 03,80,00 hdr 80
(II) PCI: 00:19:0: chip 8086,1049 card 1462,401b rev 03 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1462,401b rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1462,401b rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1462,401b rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1462,401b rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1462,401b rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1462,401b rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1462,401b rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1462,401b rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2811 card 1462,401b rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1462,401b rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2829 card 1462,401b rev 03 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1462,401b rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:04:0: chip 1180,0476 card c000,0000 rev ba class 06,07,00 hdr 82
(II) PCI: 01:04:1: chip 1180,0832 card 1462,401b rev 04 class 0c,00,10 hdr 80
(II) PCI: 01:04:2: chip 1180,0822 card 1462,401b rev 21 class 08,05,00 hdr 80
(II) PCI: 01:04:3: chip 1180,0843 card 1462,401b rev 11 class 08,80,00 hdr 80
(II) PCI: 01:04:4: chip 1180,0592 card 1462,401b rev 11 class 08,80,00 hdr 80
(II) PCI: 01:04:5: chip 1180,0852 card 1462,401b rev 11 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfe6fffff (0x900000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbdf00000 - 0xbfefffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (1:4:0), (1,2,2), BCTRL: 0x0583 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xfeb00000/20, 0xd0000000/28, I/O @ 0xec00/3
(--) PCI: (0:2:1) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0xfe900000/20
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[1] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[2] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[3] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[4] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[9] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[10] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[11] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[30] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[1] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[2] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[3] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[4] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[9] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[10] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[11] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[30] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
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
	[4] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[5] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[6] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[7] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[8] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[9] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[10] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[11] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[12] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[13] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[15] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[18] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[33] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[35] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[36] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[37] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[5] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[6] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[7] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[8] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[9] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[10] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[11] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[12] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[13] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[15] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[18] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[33] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[35] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[36] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[37] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[5] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[6] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[7] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[8] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[9] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[10] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[11] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[12] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[13] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[14] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[15] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[18] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[36] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[38] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[39] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[40] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFEB00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Generic Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video1
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00020000 to 0x00020207
(WW) intel(0): PIPEASTAT before: status: VBLANK_INT_ENABLE
(WW) intel(0): PIPEASTAT after: status: VBLANK_INT_ENABLE VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[1] 0	0	0xfeb00000 - 0xfebfffff (0x100000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfe6fec00 - 0xfe6fecff (0x100) MX[B]
	[7] -1	0	0xfe6ff000 - 0xfe6ff0ff (0x100) MX[B]
	[8] -1	0	0xfe6ff400 - 0xfe6ff4ff (0x100) MX[B]
	[9] -1	0	0xfe6ff800 - 0xfe6fffff (0x800) MX[B]
	[10] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[11] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[12] -1	0	0xfeaff000 - 0xfeaff3ff (0x400) MX[B]
	[13] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[14] -1	0	0xfeafec00 - 0xfeafefff (0x400) MX[B]
	[15] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[16] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[17] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
	[20] -1	0	0xfde01000 - 0xfde010ff (0x100) MX[B]
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] 0	0	0x0000ec00 - 0x0000ec07 (0x8) IS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[30] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[32] -1	0	0x0000e880 - 0x0000e887 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[35] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[39] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[40] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[41] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[42] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[43] -1	0	0x0000d080 - 0x0000d09f (0x20) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 489216 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1956860 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xfeb00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0100000, handle = 0xd0100000
(II) intel(0): [drm] mapped back buffer at 0xd1a00000, handle = 0xd1a00000
(II) intel(0): [drm] mapped depth buffer at 0xd2040000, handle = 0xd2040000
(II) intel(0): [drm] mapped classic textures at 0xd2680000, handle = 0xd2680000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01a00000 (pgoffset 6656)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02040000 (pgoffset 8256)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x02680000 (pgoffset 9856)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00042000-0x00042fff: overlay registers (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x0077f000:            end of stolen memory
(II) intel(0): 0x01a00000-0x0203ffff: back buffer (6400 kB) X tiled
(II) intel(0): 0x02040000-0x0267ffff: depth buffer (6400 kB) Y tiled
(II) intel(0): 0x02680000-0x0467ffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(WW) intel(0): ESR is 0x00000001
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
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
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
SetClientVersion: 0 9
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13875
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a


xorg.conf:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"     "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"Intel 965"
	Busid		"PCI:0:2:1"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "DRI"
    Mode 0666
EndSection


---

### Post by prshah on 2008-05-27
> **jamesattard said:**
> I think I noticed my problem when I did upgrade my xorg/kernel. This is my output:


You seem to be running the older driver> ```
Boardname "Intel 965"
Busid "PCI:0:2:0"
[color=red]Driver "i810"[/color]
```

Get the latest driver ```
sudo apt-get install xserver-xorg-video-intel
``` then
Change the above highlighted line (in your /etc/X11/xorg.conf file) to read```

Driver "intel"
```

then save, quit, logout, and restart X server with Ctrl+Alt+BkSpace.

---

### Post by marks_linux on 2008-05-27
trick for me was to remove the xgl so that aiglx is used.

sudo apt-get remove xserver-xgl

then restart.

---

### Post by jamesattard on 2008-05-27
Unfortunately both resolutions didn't work for me. I modified xorg.conf to use the intel driver.

---

### Post by prshah on 2008-05-27
> **jamesattard said:**
> Unfortunately both resolutions didn't work for me. I modified xorg.conf to use the intel driver.

Did you also download the latest driver using the "apt-get.." command specified before? Then restart the X server? 

If you did, lets have a look at your /etc/X11/xorg.conf...

---

### Post by jamesattard on 2008-05-27
yep apt-get reports i have the latest intel driver. xorg.conf:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Emulate3Buttons" "true"
EndSection


Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection
Section "Device"
Identifier "Configured Video Device"
Boardname "Intel 965"
Busid "PCI:0:2:0"
Driver "intel"
Screen 0
Vendorname "Intel"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection


Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Modes "1600x1200" "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "dri"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "Intel 965"
Busid "PCI:0:2:0"
Driver "i810"
Screen 1
Vendorname "Intel"
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
EndSection
Section "monitor" #
Identifier "monitor1"
Gamma 1.0
EndSection
Section "device" #
Identifier "device2"
Boardname "Intel 965"
Busid "PCI:0:2:1"
Driver "intel"
Screen 0
Vendorname "Intel"
EndSection
Section "screen" #
Identifier "screen2"
Device "device2"
Defaultdepth 24
Monitor "monitor2"
EndSection
Section "monitor" #
Identifier "monitor2"
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection
Section "DRI"
Mode 0666
EndSection

```

---

### Post by prshah on 2008-05-28
> **jamesattard said:**
> yep apt-get reports i have the latest intel driver. xorg.conf:

```

Section "Device"
Identifier "Configured Video Device"
Boardname "Intel 965"
Busid "PCI:0:2:0"
Driver "intel"
Screen 0
Vendorname "Intel"
EndSection


Identifier "device1"
Boardname "Intel 965"
Busid "PCI:0:2:0"
[color=red]Driver "i810"[/color]
Screen 1
Vendorname "Intel"
EndSection

Identifier "device2"
Boardname "Intel 965"
Busid "PCI:0:2:1"
Driver "intel"
Screen 0
Vendorname "Intel"
EndSection

```

Why do you have _three_ devices defined? And of those three, 2 refer to the same device (PCI:0:2:0). In any case, in the second instance, it's still using the old i810 driver (highlighted). Change it to read "intel" then save, exit, logout, restart with Ctrl_Alt_BkSpace.

If it works, you might try commenting out one section and seeing if you face any problems; if not, you can remove that section altogether to keep the xorg.conf "clean".

---

### Post by jamesattard on 2008-05-30
No luck yet. I am just defining this device:

```

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "Intel 965"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
        Vendorname      "Intel"
EndSection

```

---

### Post by i speak in math on 2008-05-30
I have the 965 chipset in my laptop as well, but why does my driver section only say...

Section "Device"
	Identifier	"Configured Video Device"
EndSection

I tried the apt-get update, but it said...

xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libdvbpsi4 libxosd2 libvlc0 vlc-nox libwxbase2.6-0
  libiso9660-5 vlc-plugin-pulse libtar libvcdinfo0 libebml0 libmatroska0
  libsdl-image1.2
Use 'apt-get autoremove' to remove them.

bad???

---

### Post by prshah on 2008-05-30
> **i speak in math said:**
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

bad???

Not at all bad. You must be running 8.04; In hardy the xorg.conf is "stripped". In your case, to check, press Alt+F2, then give the command ```
gksudo displayconfig-gtk
```, press enter, then check the "Graphics Card" tab; it should show "Intel experimental modesetting driver", else post back for changeover instructions.

---

### Post by jamesattard on 2008-05-30
Can someone please post me their /usr/bin/compiz script code for the Intel GM965/GL960 card? I think the problem is there...It is making checks on a previous NVIDIA card I had, and nowhere related to Intel is mentioned!

```

COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/"
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real)

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

if [ -x $METACITY ]; then
        FALLBACKWM="${METACITY}"
elif [ -x $KWIN ]; then
        FALLBACKWM="${KWIN}"
else
        FALLBACKWM=true
fi
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T=""
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS="core"
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Default X.org log if xset q doesn't reveal it
XORG_DEFAULT_LOG="/var/log/Xorg.0.log"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
        if [ "x$VERBOSE" = "xyes" ]; then
                printf "$*"
        fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
        if [ "x$SKIP_CHECKS" = "xyes" ]; then
                verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
                return 0;
        fi

        if [ "x$CM_DRY" = "xyes" ]; then
                verbose "Dry run failed: Problems detected with 3D support.'n"
                exit 1;
        fi
        verbose "aborting and using fallback: $FALLBACKWM \n"

        if [ -x $FALLBACKWM ]; then
                exec $FALLBACKWM $FALLBACKWM_OPTIONS
        else
                printf "no $FALLBACKWM found, exiting\n"
                exit 1
        fi
}

# Check for non power of two texture support
check_npot_texture()
{
        verbose "Checking for non power of two support: "
        if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
                verbose "present. \n";
                return 0;
        else
                verbose "Not present. \n"
                return 1;
        fi

}

# Check for presence of FBConfig
check_fbconfig()
{
        verbose "Checking for FBConfig: "
        if [ "$INDIRECT" = "yes" ]; then
                $GLXINFO -i | grep -q GLX.*fbconfig
                FB=$?
        else
                $GLXINFO | grep -q GLX.*fbconfig
                FB=$?
        fi

        if [ $FB = "0" ]; then
                unset FB
                verbose "present. \n"
                return 0;
        else
                unset FB
                verbose "not present. \n"
                return 1;
        fi
}


# Check for TFP
check_tfp()
{
        verbose "Checking for texture_from_pixmap: "
        if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
                verbose "present. \n"
                return 0;
        else
                verbose "not present. \n"
                if [ "$INDIRECT" = "yes" ]; then
                        unset LIBGL_ALWAYS_INDIRECT
                        INDIRECT="no"
                        return 1;
                else
                        verbose "Trying again with indirect rendering:\n";
                        INDIRECT="yes"
                        export LIBGL_ALWAYS_INDIRECT=1
                        check_tfp;
                        return $?
                fi
        fi
}

# Check wether the composite extension is present
check_composite()
{
        verbose "Checking for Composite extension: "
        if xdpyinfo -queryExtensions | grep -q Composite ; then
                verbose "present. \n";
                return 0;
        else
                verbose "not present. \n";
                return 1;
        fi
}

# Detects if Xgl is running
check_xgl()
{
        verbose "Checking for Xgl: "
        if xvinfo | grep -q Xgl ; then
                verbose "present. \n"
                return 0;
        else
                verbose "not present. \n"
                return 1;
        fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
    if [ ! -x "$NVIDIA_SETTINGS" ]; then
        return 0
    fi

        MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
        if [ $MEM -lt $NVIDIA_MEMORY ]; then
                verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
                return 1;
        fi
        return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
        if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
                return $NVIDIA_INTERNAL_TEST;
        fi
        verbose "Checking for nVidia: "
        if xdpyinfo | grep -q NV-GLX ; then
                verbose "present. \n"
                NVIDIA_INTERNAL_TEST=0
                return 0;
        else
                verbose "not present. \n"
                NVIDIA_INTERNAL_TEST=1
                return 1;
        fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
        TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
        RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
        VRES=$(echo $RESOLUTION | sed 's/.*x//')
        HRES=$(echo $RESOLUTION | sed 's/x.*//')
        verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
        if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
                verbose "Failed.\n"
                return 1;
        fi
        verbose "Passed.\n"
        return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
        LOG=$(xset q|grep "Log file"|awk '{print $3}')
        if [ "$LOG" = "" ]; then
            verbose "xset q doesn't reveal the location of the log file. Using fallback $XORG_DEFAULT_LOG \n"
            LOG=$XORG_DEFAULT_LOG;
        fi
        if [ -z "$LOG" ];then
                verbose "AIEEEEH, no Log file found \n"
                verbose "$(xset q) \n"
        return 0
        fi

        #don't run on laptops using ati driver
        if laptop-detect; then
                for DRV in ati radeon; do
                        if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
                           ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG;
                        then
                                verbose "Found laptop using ${DRV} driver. \n"
                                return 1
                        fi
                done
        fi

        for DRV in ${WHITELIST}; do
                if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
                   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG;
                then
                        return 0
                fi
        done
        verbose "No whitelisted driver found\n"
        return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
        OUTPUT=$(lspci -n)
        for ID in ${BLACKLIST_PCIIDS}; do
                if echo "$OUTPUT" | egrep -q "$ID"; then
                        verbose "Blacklisted PCIID '$ID' found \n"
                        return 0
                fi
        done
        OUTPUT=$(lspci -vn | grep -i VGA)
        verbose "Detected PCI ID for VGA: $OUTPUT\n"
        return 1
}

build_env()
{
        if check_nvidia; then
                ENV="__GL_YIELD=NOTHING "
        fi
        if [ "$INDIRECT" = "yes" ]; then
                ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
        fi
        if check_xgl; then
                if [ -f ${LIBGL_NVIDIA} ]; then
                        ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
                        verbose "Enabling Xgl with nVidia drivers...\n"
                fi
                if [ -f ${LIBGL_FGLRX} ]; then
                        ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
                        verbose "Enabling Xgl with fglrx ATi drivers...\n"
                fi
        fi

        ENV="$ENV FROM_WRAPPER=yes"

        if [ -n "$ENV" ]; then
                export $ENV
        fi
}

build_args()
{
        if [ "x$INDIRECT" = "xyes" ]; then
                COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
        fi
        if check_nvidia; then
                if [ "x$INDIRECT" != "xyes" ]; then
                        COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
                fi
        fi
####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
        test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
        test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
        test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
        test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
        abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
        INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
        # if vesa or vga are in use, do not even try glxinfo (LP#119341)
        if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
                abort_with_fallback_wm
        fi
        # check if we have the required bits to run compiz and if not,
        # fallback
        if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
                abort_with_fallback_wm
        fi

        if check_nvidia && ! check_nvidia_memory; then
                abort_with_fallback_wm
        fi

        if ! check_fbconfig; then
                abort_with_fallback_wm
        fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
        COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
        COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

if [ "x$CM_DRY" = "xyes" ]; then
        verbose "Dry run finished: everything should work with regards to Compiz and 3D.\n"
        exit 0;
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

```

---

### Post by i speak in math on 2008-05-30
My graphics card tab only lists vesa generic vesa-complient video card

---

### Post by prshah on 2008-05-30
> **i speak in math said:**
> My graphics card tab only lists vesa generic vesa-complient video card

So you need to change over: press Alt+F2, then give the command
```

gksudo displayconfig-gtk
```

Then click on "Graphics Card" Tab, then the long button next to "Driver", then "Choose driver by name", then "Intel Experimental modesetting driver" (See screenshot), Then OK.

Now you are back on the "Graphcis Card" tab, where you can either choose "Test" or "OK".

---

### Post by i speak in math on 2008-05-30
For some reason, I have to driver listings. I changed them both to intel experimental modesetting...

[ATTACH]72210[/ATTACH]

 but when I test, I just get a black and white plaid screen and need to revert back to previous settings.

[ATTACH]72211[/ATTACH]

Any ideas?

---

### Post by prshah on 2008-05-30
> **i speak in math said:**
> For some reason, I have to driver listings. I changed them both to intel experimental modesetting...
[ATTACH]72210[/ATTACH]
 but when I test, I just get a black and white plaid screen and need to revert back to previous settings.
[ATTACH]72211[/ATTACH]


Ok first, I think we need to apologize to OP for hijacking his thread.

Do you have two graphics cards on your system? One addon, and one onboard? ```
lspci | grep -i vga
``` from a terminal (Applications-Accessories-Terminal) will tell us. Or is it just that you have 2 monitors?

---

### Post by i speak in math on 2008-05-30
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 is the only listing. 

I am on a laptop so only the one monitor here unless there is a setting somewhere enabling more.

---

### Post by prshah on 2008-05-30
> **i speak in math said:**
> 
I am on a laptop so only the one monitor here unless there is a setting somewhere enabling more.

Then you must have a double entry in your /etc/X11/xorg.conf.

Your problem and OP's problems seem to be very different. I suggest you create a new thread to work further on this problem. You can start in that thread by posting your /etc/X11/xorg.conf, and the above attachments as well (which show two settings for a single video card!!)??

---

