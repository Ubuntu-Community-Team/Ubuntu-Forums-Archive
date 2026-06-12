---
title: "trying to get TV-out to work on ati all-in-wonder"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by lokimon on 2006-07-29
i built up a PIII/500mhz pc with 512MB ram, and a ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X card which seems to be from the all-in-wonder series.

followed the instructions on this thread but had no success: [http://www.ubuntuforums.org/showthread.php?t=215763](http://www.ubuntuforums.org/showthread.php?t=215763)

here is my xorg log file... i think it has the answers to my problem within it but i don't get it:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux library 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 29 11:39:37 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
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
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 1186,1300 card 1186,1301 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 12eb,0002 card 12eb,0088 rev fe class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4742 card 1002,0063 rev 5c class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x300fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc 3D Rage Pro AGP 1X/2X rev 92, Mem @ 0xe0000000/24, 0xe2000000/12, I/O @ 0xd000/8
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
	[0] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[1] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[1] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
	[4] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[5] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 6.5.8
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


```

all wouldn't fit in 1 post... continued

---

### Post by lokimon on 2006-07-29
the rest of the file:

```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.5.8) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X".
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 assigned to active "Device" section "ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X".
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[5] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers/atimisc_drv.so
(II) Module atimisc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 6.5.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[5] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[20] 0	0	0x300003b0 - 0x300003bb (0xc) IS[B]
	[21] 0	0	0x300003c0 - 0x300003df (0x20) IS[B]
(II) Setting vga for screen 0.
(==) ATI(0): Chipset:  "ati".
(**) ATI(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) ATI(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) ATI(0): VESA BIOS detected
(II) ATI(0): VESA VBE Version 2.0
(II) ATI(0): VESA VBE Total Mem: 8192 kB
(II) ATI(0): VESA VBE OEM: ATI MACH64
(II) ATI(0): VESA VBE OEM Software Rev: 1.0
(II) ATI(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) ATI(0): VESA VBE OEM Product: MACH64GT
(II) ATI(0): VESA VBE OEM Product Rev: 01.00
(II) ATI(0): VESA VBE DDC supported
(II) ATI(0): VESA VBE DDC Level none
(II) ATI(0): VESA VBE DDC transfer in appr. 2 sec.
(II) ATI(0): VESA VBE DDC read failed
(II) ATI(0): BIOS Data:  BIOSSize=0xC000, ROMTable=0x00FC.
(II) ATI(0): BIOS Data:  ClockTable=0x0828, FrequencyTable=0x0802.
(II) ATI(0): BIOS Data:  LCDTable=0x0000, LCDPanelInfo=0x0000.
(II) ATI(0): BIOS Data:  VideoTable=0x014E, HardwareTable=0x0156.
(II) ATI(0): BIOS Data:  I2CType=0x02, Tuner=0x06, Decoder=0x03, Audio=0x02.
(--) ATI(0): ATI 3D Rage Pro graphics controller detected.
(--) ATI(0): Chip type 4742 "GB", version 4, foundry UMC, class 0, revision 0x01.
(--) ATI(0): AGP bus interface detected;  block I/O base is 0xD000.
(--) ATI(0): ATI Mach64 adapter detected.
(!!) ATI(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) ATI(0): Internal RAMDAC (subtype 1) detected.
(==) ATI(0): RGB weight 888
(==) ATI(0): Default visual is TrueColor
(==) ATI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) ATI(0): Using Mach64 accelerator CRTC.
(II) ATI(0): Storing hardware cursor image at 0xE07FFC00.
(II) ATI(0): Using 8 MB linear aperture at 0xE0000000.
(!!) ATI(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) ATI(0): Using Block 0 MMIO aperture at 0xE2000400.
(II) ATI(0): Using Block 1 MMIO aperture at 0xE2000000.
(II) ATI(0): MMIO write caching enabled.
(--) ATI(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.
(II) ATI(0): Engine XCLK 100.000 MHz;  Refresh rate code 7.
(--) ATI(0): Internal programmable clock generator detected.
(--) ATI(0): Reference clock 315/11 (28.636) MHz.
(II) ATI(0): SyncMaster: Using hsync range of 30.00-50.00 kHz
(II) ATI(0): SyncMaster: Using vrefresh value of 60.00 Hz
(II) ATI(0): Maximum clock: 200.00 MHz
(II) ATI(0): Not using default mode "640x350" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x175" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x400" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x200" (vrefresh out of range)
(II) ATI(0): Not using default mode "720x400" (vrefresh out of range)
(II) ATI(0): Not using default mode "360x200" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x480" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x240" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x480" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x240" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x480" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x240" (vrefresh out of range)
(II) ATI(0): Not using default mode "800x600" (vrefresh out of range)
(II) ATI(0): Not using default mode "400x300" (vrefresh out of range)
(II) ATI(0): Not using default mode "800x600" (vrefresh out of range)
(II) ATI(0): Not using default mode "400x300" (vrefresh out of range)
(II) ATI(0): Not using default mode "800x600" (vrefresh out of range)
(II) ATI(0): Not using default mode "400x300" (vrefresh out of range)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "400x300" (hsync out of range)
(II) ATI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) ATI(0): Not using default mode "512x384" (vrefresh out of range)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using default mode "512x384" (hsync out of range)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using default mode "512x384" (hsync out of range)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using default mode "512x384" (hsync out of range)
(II) ATI(0): Not using default mode "1152x864" (hsync out of range)
(II) ATI(0): Not using default mode "576x432" (hsync out of range)
(II) ATI(0): Not using default mode "1280x960" (hsync out of range)
(II) ATI(0): Not using default mode "640x480" (hsync out of range)
(II) ATI(0): Not using default mode "1280x960" (hsync out of range)
(II) ATI(0): Not using default mode "640x480" (hsync out of range)
(II) ATI(0): Not using default mode "1280x1024" (hsync out of range)
(II) ATI(0): Not using default mode "640x512" (hsync out of range)
(II) ATI(0): Not using default mode "1280x1024" (hsync out of range)
(II) ATI(0): Not using default mode "640x512" (hsync out of range)
(II) ATI(0): Not using default mode "1280x1024" (hsync out of range)
(II) ATI(0): Not using default mode "640x512" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (hsync out of range)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (hsync out of range)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (hsync out of range)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (hsync out of range)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (hsync out of range)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (hsync out of range)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (hsync out of range)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (hsync out of range)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (hsync out of range)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (hsync out of range)
(II) ATI(0): Not using default mode "832x624" (vrefresh out of range)
(II) ATI(0): Not using default mode "416x312" (vrefresh out of range)
(II) ATI(0): Not using default mode "1152x768" (vrefresh out of range)
(II) ATI(0): Not using default mode "576x384" (vrefresh out of range)
(II) ATI(0): Not using default mode "1152x864" (hsync out of range)
(II) ATI(0): Not using default mode "576x432" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (hsync out of range)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (hsync out of range)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (hsync out of range)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1400x1050" (hsync out of range)
(II) ATI(0): Not using default mode "700x525" (hsync out of range)
(II) ATI(0): Not using default mode "1440x900" (hsync out of range)
(II) ATI(0): Not using default mode "720x450" (hsync out of range)
(II) ATI(0): Not using default mode "1600x1024" (hsync out of range)
(II) ATI(0): Not using default mode "800x512" (hsync out of range)
(II) ATI(0): Not using default mode "1680x1050" (hsync out of range)
(II) ATI(0): Not using default mode "840x525" (hsync out of range)
(II) ATI(0): Not using default mode "1680x1050" (hsync out of range)
(II) ATI(0): Not using default mode "840x525" (hsync out of range)
(II) ATI(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "840x525" (hsync out of range)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (hsync out of range)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (hsync out of range)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (hsync out of range)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (hsync out of range)
(II) ATI(0): Not using mode "1280x1024" (no mode of this name)
(II) ATI(0): Not using default mode "1280x800" (width too large for virtual size)
(II) ATI(0): Not using default mode "1280x768" (width too large for virtual size)
(--) ATI(0): Virtual size is 1024x768 (pitch 1024)
(**) ATI(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) ATI(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) ATI(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) ATI(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) ATI(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) ATI(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) ATI(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) ATI(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(==) ATI(0): DPI set to (75, 75)
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(WW) ATI(0): I2C bus Mach64 initialisation failure.
(II) ATI(0): I2C bus "Mach64" removed.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe2000000 - 0xe2000fff (0x1000) MS[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe4000000 - 0xe403ffff (0x40000) MX[B]
	[7] -1	0	0xe4040000 - 0xe40400ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[14] 0	0	0x0000d000 - 0x0000d0ff (0x100) IS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[23] 0	0	0x300003b0 - 0x300003bb (0xc) IS[B](OprU)
	[24] 0	0	0x300003c0 - 0x300003df (0x20) IS[B](OprU)
(II) ATI(0): [drm] SAREA 2200+1208: 3408
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "mach64"
(II) ATI(0): [drm] drmOpen failed
(EE) ATI(0): [dri] DRIScreenInit Failed
(II) ATI(0): Largest offscreen areas (with overlaps):
(II) ATI(0): 	1024 x 1279 rectangle at 0,768
(II) ATI(0): 	768 x 1280 rectangle at 0,768
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(**) Option "dpms"
(**) ATI(0): DPMS enabled
(WW) ATI(0): Option "TVOutput" is not used
(WW) ATI(0): Option "MonitorLayout" is not used
(II) ATI(0): Direct rendering disabled
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
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by lokimon on 2006-07-30
no ideas? very strange, cause the gatos site says the card should work.

---

### Post by lokimon on 2006-08-01
if no one has any ideas, does anyone know who else i can ask?  on aug 11th i'll be leaving this house and i'd like to have this running for them by then if possible, since no one will be likely to get it running after i leave...

---

### Post by lokimon on 2006-08-04
ok, so since i can't get any help with this issue, i am going to break down and let them put WINDOWS on the damn thing.... that's right, there should be shame, wailing and gnashing of teeth in the ubuntu community over this.

bah. windows. the shame is overwhelming right now

---

### Post by WilliamAnderson on 2007-01-16
Hi Lokimon,

I am trying to do the tv out thing with wy ATI rage 128 based card. I too have followed the instructions that you linked to and have the mostly the same results. I thought that I would reply and let you (and anyone else with pre Radeon cards) that those instructions by Stungeye are not for you. The patch that he includes does not touch the r128 driver. 

On the TV, my system corrupts the display of the Dell BIOS screen, but does display the grub messages and the inital boot messages OK. When the frame buffer starts and displays the Ubuntu logo, the TV display is also corrupt but this is easily disabled by removeng the "splash" option from the kernel options in the grub menu.lst file in /boot/grub. When X starts, the TV display goes dark and switching to a virtual termanal is corrupt on the TV. When X is shut down, either when shutting down the computer or directly, the command line terminal that worked before X started stays corrupted. If X is disabled, I can log in and use the TV as a display. It makes a nasty screen to read, but it works.

I am researching how to set a frame buffer video mode that the TV will like (may run X that way to run MythTV) and to see if I can make the r128 X driver work. 

I know that this is likely not helpful and coming way too late, but it is a start. The problem is that this is very old hardware (The Radeon I purchaced new last summer is now a "legacy" card) and few people have even tried to get TV out to work. This is the problem with using hardware that is deemed too old.  Note that the Gatos site only includes TV out in their most experimental configuration.

William

---

