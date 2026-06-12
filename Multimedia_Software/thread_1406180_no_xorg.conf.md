---
title: "no xorg.conf"
date: 2010-02-13
forum: Multimedia Software
---

### Post by DanBender on 2010-02-13
I'm trying to get my screen resolution set in Mythbuntu 9.10, but there is no xorg.conf on my system! I'm trying to figure out what to do (the xfce tool on mythbuntu doesn't offer the correct resolution, and I'm not even sure what driver I'm using).

I've seen other threads saying to run nvidia-setup or somesuch. I assume the appropriate tool in my case would be aticonfig (I saw that elsewhere too) as I'm using an ATI Radeon 9600XT, but that tool says:```
aticonfig: No supported adapters detected
```I was thinking maybe I could write an xorg.conf myself, but I don't have the first clue about what all needs to go into it. Does anyone have any ideas about this?

Thanks in advance,
-Dan

---

### Post by Yellow Pasque on 2010-02-13
> aticonfig: No supported adapters detected
You shouldn't even have this program on your system. ATI dropped support for your card in their proprietary Catalyst/fglrx drivers last year. Make sure all traces of any old drivers you tried to install are removed: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

After you restart, post/pastebin your /var/log/Xorg.0.log file. What resolution are you trying to get?

---

### Post by DanBender on 2010-02-14
Okay, I ran the terminal stuff suggested.

I'm trying to set to 1920x1080, 60Hz, the native resolution for the HDTV I'm using as a display (via VGA), [which is a supported resolution for this card (1920x1080 up to 75Hz),]("http://ati.amd.com/products/radeon9600/radeon9600pro/specs.html") at least under Windows.

here's the log file.

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux tv-computer 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=cc674928-7547-43b0-b538-8d863d1cc0fb ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 13 22:21:55 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:4152:1002:0002 ATI Technologies Inc RV350 AR [Radeon 9600] rev 0, Mem @ 0xc8000000/134217728, 0xd7cf0000/65536, I/O @ 0x00009800/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default ati Device 0"
        Driver    "ati"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default ati Screen 0"
        Device    "Builtin Default ati Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default ati Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
    ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000d7cf0000
(II) RADEON(0): MMIO registers at 0x00000000d7cf0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 9600XT AR (AGP)" (ChipID = 0x4152)
(--) RADEON(0): Linear framebuffer at 0x00000000c8000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 30000, sclk: 500.000000, mclk: 300.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=30000
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT2: INTERNAL_DAC2
  DFP1: INTERNAL_TMDS1
  DDC reg: 0x64
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using fuzzy aspect match for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1152x864
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit c8000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable primary dac
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 131072 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x0074e000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00752000
(II) RADEON(0): Will use 7480 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 7480 kb for back buffer at offset 0x00756000
(II) RADEON(0): Will use 7480 kb for depth buffer at offset 0x00ea4000
(II) RADEON(0): Will use 54272 kb for textures at offset 0x015f2000
(II) RADEON(0): Will use 54328 kb for X Server offscreen at offset 0x04af2000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x1a30; Card 0x1002/0x4152 0x1002/0x0002]
(II) RADEON(0): [agp] 32768 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7682000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7681000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf413000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xad793000
(II) RADEON(0): [drm] register handle = 0x2af9e000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xcfffc800 is: 0xcfffc800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe1ffe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 55631872 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 81620000
best_freq: 81620690
best_feedback_div: 263
best_frac_feedback_div: 0
best_ref_div: 29
best_post_div: 3
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device         USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event5"
(II)         USB Receiver: Found 9 mouse buttons
(II)         USB Receiver: Found x and y relative axes
(II)         USB Receiver: Found scroll wheel(s)
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as mouse
(II)         USB Receiver: Configuring as keyboard
(**)         USB Receiver: YAxisMapping: buttons 4 and 5
(**)         USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**)         USB Receiver: (accel) keeping acceleration scheme 1
(**)         USB Receiver: (accel) filter chain progression: 2.00
(**)         USB Receiver: (accel) filter stage 0: 20.00 ms
(**)         USB Receiver: (accel) set acceleration profile 0
(II)         USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device         USB Receiver
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event4"
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 84750000
best_freq: 84750000
best_feedback_div: 113
best_frac_feedback_div: 0
best_ref_div: 9
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using defaII) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 55631872 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 81620000
best_freq: 81620690
best_feedback_div: 263
best_frac_feedback_div: 0
best_ref_div: 29
best_post_div: 3
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device         USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event5"
(II)         USB Receiver: Found 9 mouse buttons
(II)         USB Receiver: Found x and y relative axes
(II)         USB Receiver: Found scroll wheel(s)
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as mouse
(II)         USB Receiver: Configuring as keyboard
(**)         USB Receiver: YAxisMapping: buttons 4 and 5
(**)         USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**)         USB Receiver: (accel) keeping acceleration scheme 1
(**)         USB Receiver: (accel) filter chain progression: 2.00
(**)         USB Receiver: (accel) filter stage 0: 20.00 ms
(**)         USB Receiver: (accel) set acceleration profile 0
(II)         USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device         USB Receiver
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event4"
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 84750000
best_freq: 84750000
best_feedback_div: 113
best_frac_feedback_div: 0
best_ref_div: 9
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using defaII) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 55631872 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 81620000
best_freq: 81620690
best_feedback_div: 263
best_frac_feedback_div: 0
best_ref_div: 29
best_post_div: 3
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device         USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event5"
(II)         USB Receiver: Found 9 mouse buttons
(II)         USB Receiver: Found x and y relative axes
(II)         USB Receiver: Found scroll wheel(s)
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as mouse
(II)         USB Receiver: Configuring as keyboard
(**)         USB Receiver: YAxisMapping: buttons 4 and 5
(**)         USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**)         USB Receiver: (accel) keeping acceleration scheme 1
(**)         USB Receiver: (accel) filter chain progression: 2.00
(**)         USB Receiver: (accel) filter stage 0: 20.00 ms
(**)         USB Receiver: (accel) set acceleration profile 0
(II)         USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device         USB Receiver
(**)         USB Receiver: always reports core events
(**)         USB Receiver: Device: "/dev/input/event4"
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable primary dac
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 84750000
best_freq: 84750000
best_feedback_div: 113
best_frac_feedback_div: 0
best_ref_div: 9
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc800 0xcfffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe1ffe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TV
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Found color CRT connected to primary DAC
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using defa
```This file appears to say that there are issues with that resolution. Several times, if I understand correctly (and it's entirely possible I don't). But it says there are similar problems with 1360x768, which is what it's actually, successfully running in right now.

Hope that's useful for you -- and thanks for the help!
-Dan

---

### Post by Yellow Pasque on 2010-02-14
Try starting with something basic:

```
# xorg.conf (Xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

Section "Device"
	Identifier	"Radeon9600XT"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon9600XT"
	Monitor		"Default Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1920x1080" "1360x768" "1152x864" "1024x768" "800x600" "640x480"  
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

TIP: When you're testing changes to xorg.conf, you don't have to restart the whole system. Just log out and it will restart the X server with your new settings.

---

### Post by DanBender on 2010-02-15
Okay, I may have gotten a little farther with this, but I still need some help.

I created an xorg.conf using Xorg:```
Xorg -configure
```and copied that into /etc/X11/. It boots just fine into this. Good. Still no 1920x1080 option, though. So I ran```
gdf 1920 1080 60 -x
```and it gave me the following lines I pasted into xorg.conf:```
# 1904x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 171.72 MHz
Modeline "1904x1080_60.00"  171.72  1904 2024 2232 2560  1080 1081 1084 1118  -HSync +Vsync
```This gives me a bunch of extra resolution options to select in the display manager, including 1904x1080.

Unfortunately, this is not a supported resolution for my monitor -- it needs to be 19**20**x1080 (I gave it 1920 as input...), and the horizontal frequency called out in my TV's manual is 67.5 kHz, not 67.08 as indicated in the above gtf output. It's pretty obvious what entry to change for the resolution (1904 -> 1920), but I'm not sure how to derive the dotclock entry and the other three htiming values for the change from 67.08 to 67.5 -- if that's even necessary.

If it helps, the manual states the standard for that resolution is CEA-861, not VESA.

Hopefully, I'm almost there -- either way, thanks for your help so far!

-Dan

EDIT: 2/15 23:00: AHA! I was on the right track -- kinda. Mythtv's modeline database had an entry for my TV: [http://www.mythtv.org/wiki/Modeline_Database#Sony_KDL-40W4100](http://www.mythtv.org/wiki/Modeline_Database#Sony_KDL-40W4100). That did it. Thanks for your help, [COLOR=Black]Temüjin -- I wouldn't have figured it out without the pointers on the drivers and the sample xorg.conf you posted.

Good luck to anyone else with these problems; I hope what I bumbled through here helps you out.

-Dan
[/COLOR]

---

