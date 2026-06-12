---
title: "ATI fdlrx driver install problem"
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by Pulshion on 2006-01-25
Im trying to install drivers for my x850pro agp. I followed all of the dirrections from different websites...i think i installed them sucessfully but in xorg.conf once i change driver "fdlrx" the boot hangs and doesnt load to gui it stops at terminal thing. For me to boot in gui i have to change driver eather to radeon or to ati. I ran fdlrxinfo and this is what i got ```
dmitriy@linux:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

as far as i understand it wants xfree86-dri...im not sure where to get that thing why drivers dont work? 
Thanx
Pul

---

### Post by amohanty on 2006-01-26
Have you tried the instructions here:
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

AM

---

### Post by Pulshion on 2006-01-26
yep...this is what i followed

---

### Post by amohanty on 2006-01-26
> "fdlrx"

I hope thats a typo in the post?

AM

Also if it hangs at the terminal, would it be possible for you to post the output of  /var/log/Xorg.0.log?

---

### Post by Pulshion on 2006-01-26
```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux linux 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Jan 16 17:18:08 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 26 18:11:02 2006
(==) Using config file: "/home/dmitriy/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon x850pro"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3128 card 1106,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 1102,0004 card 1102,0053 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:09:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:09:2: chip 1102,4001 card 1102,0010 rev 01 class 0c,00,10 hdr 80
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1106,0102 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4b4b card 1002,0312 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4b6b card 1002,0313 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfc00000 - 0xdfcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4b4b) rev 0, Mem @ 0xd0000000/27, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4b6b) rev 0, Mem @ 0xc8000000/27, 0xdfee0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[1] -1	0	0xdffff700 - 0xdffff7ff (0x100) MX[B]
	[2] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[3] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[6] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[1] -1	0	0xdffff700 - 0xdffff7ff (0x100) MX[B]
	[2] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[3] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[6] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[8] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffff600 - 0xdffff6ff (0x100) MX[B]
	[6] -1	0	0xdffff700 - 0xdffff7ff (0x100) MX[B]
	[7] -1	0	0xdfff8000 - 0xdfffbfff (0x4000) MX[B]
	[8] -1	0	0xdffff800 - 0xdfffffff (0x800) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[13] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
```

---

### Post by Pulshion on 2006-01-26
```
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), FireGL V3100 (RV370 5B64),
	MOBILITY RADEON X300 (M22 5460), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

---

### Post by Pulshion on 2006-01-26
Here is my xorg.conf...just in case if this is going to help any

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"glx"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load    "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon x850pro"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon x850pro"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by amohanty on 2006-01-26
your Xorg.0.conf is the log without the fglrx in the xorg.conf. What I meant was:
1. Set driver to fglrx
2. Start and watch X crash and burn
3. Copy that Xorg.0.log to some place
4. Restart with ati as driver
5. Post the copied log file from (3) 

Thanks.
AM

---

### Post by Pulshion on 2006-01-26
I think i got the right xorg log right now. I didnt do what you told me though. I found xorg.0.log.old and i looked through it and it seems like its the error. Sorry that i posted the wrong one before. Somehow i reinstalled the proprietory drivers and i got my xorg.conf placed in /home/dmitriy/xorg.conf

Updated the top posts....

Thanx
Pul

---

### Post by amohanty on 2006-01-26
Ok you need to specify which PCI bus has your card attached here:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon x850pro"
	Driver		"fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
EndSection
```

Per the error:
> (WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
your video card is set into the second PCI slot. So change the top quoted section to:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon x850pro"
	Driver		"fglrx"
        **BusID          "PCI:1:0:1" **
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
EndSection
```

The newly added part is in bold. That should do it. If that doesnt work, run :
> sudo dpkg-reconfigure xorg-xserver
and other than selecting fglrx just default through everything else.

HTH
AM

---

### Post by Pulshion on 2006-01-27
thanx for helping me to solve the problem, i did get a little bit confused about my slot id's. My vga is AGP what would be its id? Because i believe in the code you stated it tells me the PCI slot

---

### Post by amohanty on 2006-01-27
From the X documentation: [http://ftp.x.org/pub/X11R7.0/doc/html/xorg.conf.5.html#toc7](http://ftp.x.org/pub/X11R7.0/doc/html/xorg.conf.5.html#toc7)

> BusID "bus-id"
    This specifies the bus location of the graphics card. For PCI/AGP cards, the bus-id string has the form PCI:bus:device:function (e.g., "PCI:1:0:0" might be appropriate for an AGP card). This field is usually optional in single-head configurations when using the primary graphics card. In multi-head configurations, or when using a secondary graphics card in a single-head configuration, this entry is mandatory. Its main purpose is to make an unambiguous connection between the device section and the hardware it is representing. This information can usually be found by running the Xorg server with the -scanpci command line option.

As to why AGP still goes to PCI, you got me there. Unfortunately I am not enough of a system level guru to be able to answer that question.

HTH
AM

---

### Post by Pulshion on 2006-01-27
Thanx again, but unfortunately i still got no luck. I did what you told me and it still displayes that device not found. I tried both 1:0:0 and 1:0:1. I guess there is another id for my agp. Is there a command that shows all of the busses that are on my computer?

"This information can usually be found by running the Xorg server with the -scanpci command line option." What command would i need to type in terminal?

That error thing keep saying that "for instance  bus (1:0:1)" and if i put this bus in my xorg then i get  "for instance  bus (1:0:0)" I have a sound card plugged in my pci slot and agp. Those are the only plugged in. Could they both be conflicting? As far as i understand when i rad the "Why linux is for you" It mensioned something about having 3 things and they are screen, vga, and monitor or something. I dont remember exactly

Thanx 
pul

---

### Post by unsane on 2006-01-27
Hi y'all

Its fun how I get almost the same error (although my Bus-Id is 3:0:0 and 3:0:1 respectively :???:  ) with an x850 xt (AGP). And yes, the chip-ID is wrong too. 
I have tried numerous approaches, but everything just makes X whimper out and leaves me in textmode to dpkg...

[COLOR="Red"]<rant="skip if easily offended">[/COLOR]

I have killed X so many times ATI owes me the card for free... Unfortunately I spent the equivalent of $400 on it already.
From what I gather around the net ATI dropped the ball here, and made a driver that is useless for x850 owners. Good they got my money this time, because next time it'll be nVidia for sure. ATI makes great cards, but alas... I have no 3D accelleration at all, and hardly any in 2D either. Need I say the card literally smokes in Windows (dons flameretardent suit)? I have given up on it... Unless the boss from ATI's Linux dept. personally shows up here and shows me I'm a tard; this will be my last Ati: since moving over to Linux means more to me than supporting incompetent hardware vendors. 
Anyway, yes, I'm a Linux noob, but I can get around it fairly easy. I do have quite some competence in Windåhs. I can read and follow a How-To if thats necessary... But if several How-To's written by people who know more of Linux than me, just fails to install a friggin videodriver, then the fault is not on me, or the people who wrote the How-To's, but the software... Namely Ati's software; not Ubuntu, mind you ;-). 
I have seen people everywhere having the same ridiculous errors on all kinds of distros...
My wife owns an nVidia FX 5200; she is as new to Linux as I am (a bit more even), she had a driver installed in ~5 minutes... I have spent days... 
I'd say this though: ATI: Leave the driver source-code to the community, and they'd probably sort this out in a forthnight...:twisted: 
[COLOR="Red"]
</rant>[/COLOR]

[QUOTE=amohanty]
As to why AGP still goes to PCI, you got me there. Unfortunately I am not enough of a system level guru to be able to answer that question.
[/QUOTE]

Because, in essence, AGP is just PCI on steroids. And PCI-E is PCI on even stronger steroids.

---

### Post by amohanty on 2006-01-27
unsane I feel for you... but then again thats what craigslist is for :) video cards incomaptible with linux...

try:

> scanpci -v
and post the outputs

AM

---

### Post by Pulshion on 2006-01-27
I tried scanpci -v in terminal but it didnt work and it says that command not found. I will try to change id to 3:0:0 and 3:0:1. Im trying to install damn drivers for like 3rd day already and nothing.

Edit:
I tried both 3:0:0 and :1, I ended up getting both of the errors:

No Matching device section for instance (BusID 1:0:0)
No Matching device section for instance (BusID 1:0:1)

So my video card is on one of them...i guess

---

### Post by amohanty on 2006-01-27
OK then try this int he console:

> sudo X -scanpci 

or if that fails try:

> sudo X :0 -scanpci 


AM

---

### Post by Pulshion on 2006-01-27
```

dmitriy@linux:~$ sudo X -scanpci

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.X.Org
 for help.

```
```

dmitriy@linux:~$ sudo X :0 -scanpci
Password:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.X.Org
 for help.


```

---

### Post by jimbo2150 on 2006-01-27
I do not believe there is anything you can do to alleviate the problem.

From reading through numerous forums I found nothing that worked for myself.

From what I gather, Linux and ATI do not mix (wheather on Ubuntu or any other Linux distrib.). The drivers for it (ATI's or the res. modules) do not work (in most cases). You are basically considered extremely lucky if X accepts it.

Apparently us ATI users have nothing to do but wait for the ATI Linux team to make drivers that work with Linux. Unfortunate and Ironic. I used to be an Nvidia person (with Windows), then I became an ATI person (when NVidia Win drivers started failing), now ATI drivers do not work with Linux (which I am using now) and now Im just POed in general.

I suppose I can live without 3D for a while. Everything else like music, video, etc seem to work fine. The 3D runs really slow though.

---

### Post by Pulshion on 2006-01-27
That sucks so bad...i wanted to switch to full linux. There is gotta be a way to have drivers. Its impossible...dont stupid ATI people check drivers b4 they put them up? I saw some people that run ati cards on linux...Ok...ill just go cry in the bathroom

---

### Post by amohanty on 2006-01-27
Try to do it from the recovery console, not after you have logged in .

AM

Edit: BTW I have a Radeon X300SE (quite cheapo but works for my windows games) and it works fine except for switching users in X.

---

### Post by unsane on 2006-01-28
[QUOTE=amohanty]unsane I feel for you... but then again thats what craigslist is for :) video cards incomaptible with linux...

try:


and post the outputs

AM[/QUOTE]

I tried, and got the same output as Pulshion... Thats why I posted here, because I got the same laughable results on an almost similar card (and frankly, I felt a slight need to bitch about it..). Its a bit like ATI sold me a Ferrari with square wheels...
I've lost track of what I tried until now... Actually I promised myself, for the sake of domestic peace, to not touch it until: A) Ati puts out a new driver that actually works.. or B) Someone more knowledgeable in Linux than me sorts it out for me... I've lost confidence in A) though, since both the market and support for AGP cards seems to be fading faster than... Well, whatever fades *real* fast :rolleyes: Talk about forced upgrade... 
If I want 3D acceleration, I guess I'll just boot into Windows, and see my card beat any competition in the AGP field. To bad the quality of the proprietary software doesn't live up to the hardware... Its too bad though, I'd really like to ditch Windows, but since I game a lot Win seems to be a must... I've been happy with ATi cards; my old retired 9700 did better than a lot of newer models, and expect this one here to have the same ridiculous lifespan, but even in Windows it seems that tweaked non-ATIdrivers perform better... Ok, I'll shut up now :-D

On edit:
I failed miserably at getting output from recovery mode to file... Heres what I got in relevance to the card using good old lo-tech means:

```


(3:0:0) Unknown card (0x1002/0x0312) using an unknown chip DeviceID (0x4b49) from Ati Technologies, Inc.
(3:0:1) Unknown card (0x1002/0x0313) using an unknown chip DeviceID (0x4b69) from Ati Technologies, Inc.


```

---

### Post by amohanty on 2006-01-28
Ok then try adding> BusID    "PCI:3:0:1"

to the adapter device section. If that doesnt work try putting in 3:0:0. If nothing works, stick with the default ATI driver, throw fglrx out the window. I dual boot too, and only so that I can play games on windows, and this is something lots of ppl do. Unfortunately that seems to be the only option. If you are a serious gamer, invest in a console is all I can say.

:) Ranting is good. Much better then exploding ad wrecking your 19" LCD (yup seen that happen too)

AM

---

### Post by unsane on 2006-01-29
AFA I can see its already there... Here xorg.conf is in all its (imagined and wee bit hacked) glory...

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATi Radeon X850XT"
	Driver		"ati"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATi Radeon X850XT"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

``` 

As I said; I really don't care about 3D in Ubuntu anymore (yes, I have given up)... I'd just like to have the same control over my desktop as in Win; so that if I for instance change my resolution, it doesnt make the desktop area shrink on my 19'' (CRT ;) ).
OT:
On consoles... If money grew in my backyard, I'd prolly have one of each kind, but as it is, a pc with its capability of easily upgrade of specific pieces of hardware along the way, sure beats buying a new xbox and/or Playstation every other year.
Personally I see consoles as kind of a scam, and only an option for the 'casual gamer'. Consoles, generally, is a mess of patents and DRM's and exclusive titles. So I want to play game 'X', its on console A... I'd also like to try out game Y, oh my, its on console B. And that game might look fun for my daughter, hey, its on console C... Theres a reason why Sony and Microsoft are so happy about their consoles, and I have a nagging suspicion its the same reason why I'm not too enticed about the whole shebang. Somehow it even pipes nicely into the reasons why I want to leave MS and Gates out in the cold... And this is turning into a nice example of thread hi-jacking :-#

---

### Post by m0unds on 2006-01-29
[http://www.rage3d.com/board/showthread.php?t=33834517]("http://www.rage3d.com/board/showthread.php?t=33834517")


there's an issue with the fglrx kernel module not including the chipid's for a lot of the x8xx series cards-- there's a few threads on these boards as well as rage3d about it. I'm in the same boat-- i got it work in 2D, but DRI is still borked. I'm gonna try hex editing the kernel module to add my chip ID.

---

### Post by unsane on 2006-01-29
Yup... Think I've seen that thread before... I might try it out when I get the time. If you try it, and it works, I hope you'll post back here and let us know (how :-P).

---

### Post by Skye on 2006-01-29
I think I might have a (partial) solution.

To those of you with the incorrect BusID option, do the following in a terminal:
```
lspci
```

Somewhere in the lines of code that pop out, you will get something that looks like this:

```
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
```

This is from my machine, which is a laptop with an ATi 200m video processor.  Note how it says **0000:01:05.0** in the beginning-  I checked my xorg.conf, and the numbers match up.  0000:01:05.0 is translated into  **BusID       "PCI:1:5:0"**.

As to the other problems, I don't really know enough to help.  Although I do have an ATi card, I also have a 2.6.15.1 kernel, which breaks the dri portion of the fglrx driver- and my software suspend driver is broken by the fglrx driver.  So, i'm stuck with mesa acceleration for now, but good luck to you guys!

---

### Post by Pulshion on 2006-01-30
Well....thanx everybody for trying to help out, i really appreciate it. I can see that its not only me that is having problems with ati. I hope something will be changed and i can enjoy linux in 3d. But for now i will forget linux for awhile and support bill gates for a couple years unstill A. I get nvidia(aint gonna happen i just got this card) B: ATI comes out with new drivers. C: Bill Gates dies D: End of the world. No going full linux to lan party anymore :(.

---

### Post by unsane on 2006-01-30
Too bad, though... Why dont you do like everyone else and dual-boot? That way you can have the best of both worlds; a safe environment in which you can browse the web and read your emails, and a Windoze partition for the games that need it (which, I might add, is the only thing Windows is good for anyway... How that POS came to be the leading OS of the world has more to do with shady/illegal business methods, than actual quality of the OS, that is established fact...).

---

### Post by Marauder1 on 2006-01-30
Same thing here with my bran new X850 pro. I will try the device chip ID editor or
else i will drop that back to the store and get an Nvidia base card.

---

### Post by ageros on 2006-01-30
Hi guys, just as a final note. I've been doing some driver and chipID hacks on my x850 for the past couple of weeks, and then I happened to noticed that my X850 contains the r481 chipset. The ATI drivers, however, only list the R480 chipsets as being supported. I don't know if this has any real relevance, but in believe this is the root of the DRI issue.

I added ChipID   0X5D4F to my options under the device menu in xorg.conf and I was able to load X with the fglrx driver, but was not able to get DRI, give that a shot and see what happens.

---

### Post by Pulshion on 2006-01-30
I was thinking to get eather 6800gt oc from bfg or x850pro. Then i decided to go with x850pro because i though i can get the same performance by unlocking 4 pipes and overclocking it. I am very happy with my card. But i havent tried linux before so i though ill be fine with ati. I think there is a way to get my card working on ubuntu or other linuxes There are tons of people using ati on linuxes. I do have a dual boot setup right now but i dont see the reason why i would want to use linux if everything i do and need to do i can do on windows. I wish everyone just united and made one perfect os so everyone is happy. 
ageres...do you have agp card right? Ill give it a shot anyway, nothing to lose, eh. Thanx.

---

### Post by ageros on 2006-01-31
Yes, I am using the AGP card.

If nothing else I prefer using Linux more, because I have the freedom to do whatever I want. I can modify and change things as much as I want. For example today I spent forever on the phone getting a customer's new XP install activated, because the first one crashed. That was just pure annoyance to me, and frankly did not make me very happy. Why should I have to call and get something reactivated because they didn't program it right in the first place?

All around I've found that Linux itself is much more stable. If I ever have a problem its because I'm either 1. using beta software or 2. I did something I was told not to.

Right now the one thing that is going to keep sending people back to windows is the lack of vendor support. ATI is a perfect example. While they "support" Linux they obviously don't care that much seeing as how the new x1900s are out, and yet the old x850(r481) chipset is not supported.

Either way the one thing you do gain with Linux is security, no spyware, and not enough virus threats to even be worth the worry. Considering I have just as easy of a time using Linux as I do windows I honestly can't stand using it anymore(though I am still fond of Macs).

---

### Post by unsane on 2006-01-31
> **Pulshion] I do have a dual boot setup right now but i dont see the reason why i would want to use linux if everything i do and need to do i can do on windows. I wish everyone just united and made one perfect os so everyone is happy. [/QUOTE]

Look at it this way: Try putting an unpatched, unfirewalled not-AV-protected Windows machine on ADSL online, then set up OE and read your emails, maybe surf a little. If the machine is still usable after say a couple of hours you're pretty lucky. Whats the fun in RE-re-installing a system because it was online for 20 minutes, unsecured? Been there, done that.
Try doing the same with a Linux box. Now, naturally I am going to look at IP-tables but for the last week the only security I've had here on Ubuntu is my NAT-router.
On my windows partition I have Zonealarm, NOD32, Spybot (with registry monitoring) + various other on-demand programs and measures just to keep the OS up and running. 
And that is just security... Theres lot of other stuff I could argument with.
Now, get me right said:**
> 
Right now the one thing that is going to keep sending people back to windows is the lack of vendor support. ATI is a perfect example. While they "support" Linux they obviously don't care that much seeing as how the new x1900s are out, and yet the old x850(r481) chipset is not supported.

Either way the one thing you do gain with Linux is security, no spyware, and not enough virus threats to even be worth the worry. Considering I have just as easy of a time using Linux as I do windows I honestly can't stand using it anymore(though I am still fond of Macs).

I'm with you there. It bothers me immensely that I have to keep an operating system because 20 years of ugly business practice has made it an exclusive player. These days there's all kinds of talk about 'freedom' and stuff... So why can't I use my videocard and my printer?
We can only hope that more and more people will use Linux, open formats and so on, and base their purchases on that choice. They won't listen to me (us), but they will need my (our) damn money if they want to stay in business. I actually contemplate writing to ATI telling them that unless their Linux support is at least on par with their Windows support, my next purchase will be from their competitor.
I do know no-one will ever read it, but still. If they got, say, 10000 of these emails at once, they might start getting it....
Oh well, I ramble again....

---

### Post by Pulshion on 2006-01-31
Ageros, i tried your method but it didnt work, how can i check the id of a my chip? Im trying to get my card swapped for maybe 6800gt/oc. Ill see if i get this thing solved, which i think is a posibility. I been doing alot of reasearches and so far nothing. I wouldnt mind 6800gt/oc i was about to buy it, but i got a nice deal on x850pro.

---

### Post by Pulshion on 2006-02-16
Bump

---

