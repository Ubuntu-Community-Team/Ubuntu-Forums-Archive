---
title: "Drivers for AGP and PCI card not loading"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by sdoyle on 2006-06-05
Loaded Dapper today.  Screen is slow.

I have an ATI graphics chipset build-into the motherboard, but I use a PCI card for graphics because it is the only thing compatible with my non-standard LCD monitor.

The AGP drivers seem to be loading, while the PCI drivers don't.

```
workstation:~$ lsmod | grep ati
cpufreq_conservative     9000  0
snd_atiixp             21324  1
snd_ac97_codec         99808  1 snd_atiixp
snd_pcm                96676  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd                    60004  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11304  2 snd_atiixp,snd_pcm
**ati_agp**                 9740  1
**agpgart**                36784  1 ati_agp
**atiixp**                  7152  1
```

The PCI card is an ATI Rage LT Pro, which should be loading the **atimisc** driver.  I tried adding the line "atimisc" to /etc/modules, without effect.

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
atimisc

```

The problem seems to be related to having a PCI card and AGP chipset in use at the same time.  See [http://ubuntuforums.org/showthread.php?t=181349](http://ubuntuforums.org/showthread.php?t=181349)

So, maybe if I could disable the AGP chipset, the other would load ok?  If so, how would I do this?

Here is my xorg.conf...

```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. 3D Rage LT Pro"
        Driver          "ati"
        BusID           "PCI:2:7:0"
EndSection

Section "Monitor"
        Identifier      "PGS DPP800"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. 3D Rage LT Pro"
        Monitor         "PGS DPP800"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

And here is the output from the X log...

```
workstation:~$ cat /var/log/Xorg.0.log

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux workstation 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  5 17:06:33 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PGS DPP800"
(**) |   |-->Device "ATI Technologies, Inc. 3D Rage LT Pro"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux

(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7
(--) PCI:*(2:7:0) ATI Technologies Inc 3D Rage LT Pro rev 220, Mem @ 0xec000000/24, 0xed021000/12, I/O @ 0xd800/8

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
(II) Primary Device is: PCI 02:07:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. 3D Rage LT Pro".
(II) ATI:  Shared PCI/AGP Mach64 in slot 2:7:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 2:7:0 assigned to active "Device" section "ATI Technologies, Inc. 3D Rage LT Pro".
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xed022000 - 0xed0227ff (0x800) MX[B]
        [5] -1  0       0xed020000 - 0xed0200ff (0x100) MX[B]
        [6] -1  0       0xee105000 - 0xee1050ff (0x100) MX[B]
        [7] -1  0       0xee103000 - 0xee1033ff (0x400) MX[B]
        [8] -1  0       0xee102000 - 0xee102fff (0x1000) MX[B]
        [9] -1  0       0xee101000 - 0xee101fff (0x1000) MX[B]
        [10] -1 0       0xee100000 - 0xee100fff (0x1000) MX[B]
        [11] -1 0       0xee104000 - 0xee103fff (0x0) MX[B]O
        [12] -1 0       0xed021000 - 0xed021fff (0x1000) MX[B](B)
        [13] -1 0       0xec000000 - 0xecffffff (0x1000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [17] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers/atimisc_drv.so
(II) Module atimisc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xed022000 - 0xed0227ff (0x800) MX[B]
        [5] -1  0       0xed020000 - 0xed0200ff (0x100) MX[B]
        [6] -1  0       0xee105000 - 0xee1050ff (0x100) MX[B]
        [7] -1  0       0xee103000 - 0xee1033ff (0x400) MX[B]
        [8] -1  0       0xee102000 - 0xee102fff (0x1000) MX[B]
        [9] -1  0       0xee101000 - 0xee101fff (0x1000) MX[B]
        [10] -1 0       0xee100000 - 0xee100fff (0x1000) MX[B]
        [11] -1 0       0xee104000 - 0xee103fff (0x0) MX[B]O
        [12] -1 0       0xed021000 - 0xed021fff (0x1000) MX[B](B)
        [13] -1 0       0xec000000 - 0xecffffff (0x1000000) MX[B](B)
        [14] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [21] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [22] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
        [24] 0  0       0x200003b0 - 0x200003bb (0xc) IS[B]
        [25] 0  0       0x200003c0 - 0x200003df (0x20) IS[B]
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
(II) ATI(0): VESA VBE Total Mem: 8128 kB
(II) ATI(0): VESA VBE OEM: ATI MACH64
(II) ATI(0): VESA VBE OEM Software Rev: 1.0
(II) ATI(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) ATI(0): VESA VBE OEM Product: MACH64LP
(II) ATI(0): VESA VBE OEM Product Rev: 01.00
(II) ATI(0): VESA VBE DDC supported
(II) ATI(0): VESA VBE DDC Level 2
(II) ATI(0): VESA VBE DDC transfer in appr. 2 sec.
(II) ATI(0): VESA VBE DDC read successfully
(II) ATI(0): Manufacturer: PGS  Model: eb  Serial#: 143
(II) ATI(0): Year: 1999  Week: 23
(II) ATI(0): EDID Version: 1.2
(II) ATI(0): Digital Display Input
(II) ATI(0): Max H-Image Size [cm]: horiz.: 36  vert.: 29
(II) ATI(0): Gamma: 2.20
(II) ATI(0): DPMS capabilities: Off; RGB/Color Display
(II) ATI(0): First detailed timing is preferred mode
(II) ATI(0): redX: 0.568 redY: 0.329   greenX: 0.300 greenY: 0.600
(II) ATI(0): blueX: 0.140 blueY: 0.090   whiteX: 0.304 whiteY: 0.313
(II) ATI(0): Manufacturer's mask: 0
(II) ATI(0): Supported Future Video Modes:
(II) ATI(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) ATI(0): Supported additional Video Mode:
(II) ATI(0): clock: 108.0 MHz   Image Size:  359 x 287 mm
(II) ATI(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) ATI(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) ATI(0): Supported additional Video Mode:
(II) ATI(0): clock: 74.2 MHz   Image Size:  359 x 287 mm
(II) ATI(0): h_active: 1280  h_sync: 1392  h_sync_end 1432 h_blank_end 1648 h_border: 0
(II) ATI(0): v_active: 1024  v_sync: 1029  v_sync_end 1034 v_blanking: 1054 v_border: 0
(II) ATI(0): Monitor name: PGS DPP800
(II) ATI(0): Serial No: THCY2300143
(II) ATI(0): BIOS Data:  BIOSSize=0x10000, ROMTable=0x010C.
(II) ATI(0): BIOS Data:  ClockTable=0x0908, FrequencyTable=0x08E2.
(II) ATI(0): BIOS Data:  LCDTable=0x0184, LCDPanelInfo=0xDD8A.
(II) ATI(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0156.
(II) ATI(0): BIOS Data:  I2CType=0x03, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) ATI(0): ATI 3D Rage LT Pro graphics controller detected.
(--) ATI(0): Chip type 4C49 "LI", version 4, foundry UMC, class 0, revision 0x03.
(--) ATI(0): PCI bus interface detected;  block I/O base is 0xD800.
(--) ATI(0): ATI Mach64 adapter detected.
(!!) ATI(0): For information on using the multimedia capabilities
        of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) ATI(0): Internal RAMDAC (subtype 1) detected.
(==) ATI(0): RGB weight 888
(==) ATI(0): Default visual is TrueColor
(==) ATI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) ATI(0): Using Mach64 accelerator CRTC.
(!!) ATI(0): Invalid horizontal sync pulse timing detected in mode on server entry.
(--) ATI(0): 1280x1024 panel (ID 1) detected.
(--) ATI(0): Panel model PGS.
(--) ATI(0): Panel clock is 74.365 MHz.
(II) ATI(0): Using digital flat panel interface.
(II) ATI(0): Storing hardware cursor image at 0xEC7FFC00.
(II) ATI(0): Using 8 MB linear aperture at 0xEC000000.
(!!) ATI(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) ATI(0): Using Block 0 MMIO aperture at 0xED021400.
(II) ATI(0): Using Block 1 MMIO aperture at 0xED021000.
(II) ATI(0): MMIO write caching enabled.
(--) ATI(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.
(II) ATI(0): Engine XCLK 100.023 MHz;  Refresh rate code 7.
(--) ATI(0): Internal programmable clock generator detected.
(--) ATI(0): Reference clock 29.500 MHz.
(WW) ATI(0): Extraneous XF86Config HorizSync specification(s) ignored.
(!!) ATI(0): Conflicting XF86Config VertRefresh specification(s) ignored.
(II) ATI(0): Maximum clock: 200.00 MHz
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (exceeds panel dimensions)
(--) ATI(0): Virtual size is 1280x1024 (pitch 1280)
(**) ATI(0): *Default mode "1280x1024": 74.4 MHz, 44.1 kHz, 41.6 Hz
doublescan +hsync -vsync
(--) ATI(0): Display dimensions: (360, 290) mm
(--) ATI(0): DPI set to (90, 89)
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
        [0] 0   0       0xed021000 - 0xed021fff (0x1000) MS[B]
        [1] 0   0       0xec000000 - 0xecffffff (0x1000000) MS[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xed022000 - 0xed0227ff (0x800) MX[B]
        [7] -1  0       0xed020000 - 0xed0200ff (0x100) MX[B]
        [8] -1  0       0xee105000 - 0xee1050ff (0x100) MX[B]
        [9] -1  0       0xee103000 - 0xee1033ff (0x400) MX[B]
        [10] -1 0       0xee102000 - 0xee102fff (0x1000) MX[B]
        [11] -1 0       0xee101000 - 0xee101fff (0x1000) MX[B]
        [12] -1 0       0xee100000 - 0xee100fff (0x1000) MX[B]
        [13] -1 0       0xee104000 - 0xee103fff (0x0) MX[B]O
        [14] -1 0       0xed021000 - 0xed021fff (0x1000) MX[B](B)
        [15] -1 0       0xec000000 - 0xecffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [19] 0  0       0x0000d800 - 0x0000d8ff (0x100) IS[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [23] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [24] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [25] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [26] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
        [27] 0  0       0x200003b0 - 0x200003bb (0xc) IS[B](OprU)
        [28] 0  0       0x200003c0 - 0x200003df (0x20) IS[B](OprU)
(WW) ATI(0): DRI static buffer allocation failed -- need at least 12800 kB video memory
(II) ATI(0): Largest offscreen areas (with overlaps):
(II) ATI(0):    1280 x 614 rectangle at 0,1024
(II) ATI(0):    256 x 615 rectangle at 0,1024
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                20 128x128 slots
                5 256x256 slots
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(**) Option "dpms"
(**) ATI(0): DPMS enabled
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
(**) Option "XkbVariant" "dvorak"
(**) Generic Keyboard: XkbVariant: "dvorak"

```

Any other ideas?  Thank you for reading this far :-)

---

### Post by sdoyle on 2006-06-06
Ok, so I fixed it.  Here are the steps:

1. Go into the BIOS and ensure that it is booting with the PCI card instead of the AGP chipset.

2. Set the "AGP aperature" BIOS setting to a size bigger than the RAM on the PCI card.  In my case, I have 8MB of video card memory and I set the aperature size to 32MB.

3. Reboot and look at "/var/log/Xorg.0.log".  If there is a problem, you can see what it is here.  In my case it said that I didn't have enough video memory to enable DRI.

4. Edit "/etc/X11/xorg.conf".  Go into the "Screen" section and change the "DefaultDepth" setting to cut the video memory requirements down.  I was running at 1280x1024x24.  I changed the DefaultDepth to 16.

5. Reboot and look at the "/var/log/Xorg.0.log" setting again.  You should see that DRI is enabled.

Hope this helps someone.  Apparently Dapper is causing a lot of problems for people with ATI cards.

---

