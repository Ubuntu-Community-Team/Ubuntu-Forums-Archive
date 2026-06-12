---
title: "Display Size"
date: 2011-08-19
forum: Multimedia Software
---

### Post by sffuji on 2011-08-19
Hi,

In Ubuntu 11.04, all windows display larger than the available screen size, and I haven't found a way to make them fit within the display area of the monitor.  This is a Dell 19" flat screen monitor, and I've tried changing the display; no matter what resolution is selected, the windows all bleed past the screen.  Any ideas?

Thanks!

---

### Post by papibe on 2011-08-19
I suspect that the monitor doesn't inform correctly to the card its correct resolutions and timings (corrupt [EDID]("http://en.wikipedia.org/wiki/EDID") maybe?). 

Could you post your X11's log? It is the file /var/log/Xorg.0.log

Regards.

BTW: I have a Dell 19" flat screen monitor too. Everything OK here, though.

---

### Post by BicyclerBoy on 2011-08-19
Try DVI connection..

VGA EDID reporting seems to be getting more broken every week..

---

### Post by sffuji on 2011-08-20
Here are the contents of my current xorg log (I tried to upload it but got an invalid file message)

[    13.864] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.864] X Protocol Version 11, Revision 0
[    13.864] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    13.864] Current Operating System: Linux ml-Dimension-9100 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    13.864] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=bc732635-0f83-4572-bc72-249efec5c269 ro quiet splash vt.handoff=7
[    13.864] Build Date: 19 April 2011  03:33:17PM
[    13.864] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.864] Current version of pixman: 0.20.2
[    13.864]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    13.864] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.865] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 19 18:35:28 2011
[    14.173] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.174] (==) No Layout section.  Using the first Screen section.
[    14.174] (==) No screen section available. Using defaults.
[    14.174] (**) |-->Screen "Default Screen Section" (0)
[    14.174] (**) |   |-->Monitor "<default monitor>"
[    14.174] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.174] (==) Automatically adding devices
[    14.174] (==) Automatically enabling devices
[    14.174] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.174]     Entry deleted from font path.
[    14.174] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.174]     Entry deleted from font path.
[    14.174] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.174]     Entry deleted from font path.
[    14.175] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.175]     Entry deleted from font path.
[    14.175] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.175]     Entry deleted from font path.
[    14.175] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.175] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.175] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.175] (II) Loader magic: 0x81ffde0
[    14.175] (II) Module ABI versions:
[    14.175]     X.Org ANSI C Emulation: 0.4
[    14.175]     X.Org Video Driver: 10.0
[    14.175]     X.Org XInput driver : 12.3
[    14.175]     X.Org Server Extension : 5.0
[    14.176] (--) PCI:*(0:1:0:0) 1002:5b60:1002:0302 rev 0, Mem @ 0xf0000000/134217728, 0xfe9e0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
[    14.176] (--) PCI: (0:1:0:1) 1002:5b70:1002:0303 rev 0, Mem @ 0xfe9f0000/65536
[    14.176] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.176] (II) LoadModule: "extmod"
[    14.216] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.277] (II) Module extmod: vendor="X.Org Foundation"
[    14.277]     compiled for 1.10.1, module version = 1.0.0
[    14.277]     Module class: X.Org Server Extension
[    14.277]     ABI class: X.Org Server Extension, version 5.0
[    14.277] (II) Loading extension MIT-SCREEN-SAVER
[    14.277] (II) Loading extension XFree86-VidModeExtension
[    14.277] (II) Loading extension XFree86-DGA
[    14.277] (II) Loading extension DPMS
[    14.277] (II) Loading extension XVideo
[    14.277] (II) Loading extension XVideo-MotionCompensation
[    14.277] (II) Loading extension X-Resource
[    14.278] (II) LoadModule: "dbe"
[    14.278] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.279] (II) Module dbe: vendor="X.Org Foundation"
[    14.279]     compiled for 1.10.1, module version = 1.0.0
[    14.279]     Module class: X.Org Server Extension
[    14.279]     ABI class: X.Org Server Extension, version 5.0
[    14.279] (II) Loading extension DOUBLE-BUFFER
[    14.279] (II) LoadModule: "glx"
[    14.279] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.280] (II) Module glx: vendor="X.Org Foundation"
[    14.280]     compiled for 1.10.1, module version = 1.0.0
[    14.280]     ABI class: X.Org Server Extension, version 5.0
[    14.280] (==) AIGLX enabled
[    14.280] (II) Loading extension GLX
[    14.280] (II) LoadModule: "record"
[    14.281] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.281] (II) Module record: vendor="X.Org Foundation"
[    14.281]     compiled for 1.10.1, module version = 1.13.0
[    14.281]     Module class: X.Org Server Extension
[    14.281]     ABI class: X.Org Server Extension, version 5.0
[    14.281] (II) Loading extension RECORD
[    14.281] (II) LoadModule: "dri"
[    14.282] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.282] (II) Module dri: vendor="X.Org Foundation"
[    14.282]     compiled for 1.10.1, module version = 1.0.0
[    14.282]     ABI class: X.Org Server Extension, version 5.0
[    14.282] (II) Loading extension XFree86-DRI
[    14.282] (II) LoadModule: "dri2"
[    14.289] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.290] (II) Module dri2: vendor="X.Org Foundation"
[    14.290]     compiled for 1.10.1, module version = 1.2.0
[    14.290]     ABI class: X.Org Server Extension, version 5.0
[    14.290] (II) Loading extension DRI2
[    14.290] (==) Matched fglrx as autoconfigured driver 0
[    14.290] (==) Matched ati as autoconfigured driver 1
[    14.290] (==) Matched vesa as autoconfigured driver 2
[    14.290] (==) Matched fbdev as autoconfigured driver 3
[    14.290] (==) Assigned the driver to the xf86ConfigLayout
[    14.290] (II) LoadModule: "fglrx"
[    14.384] (WW) Warning, couldn't open module fglrx
[    14.385] (II) UnloadModule: "fglrx"
[    14.385] (II) Unloading fglrx
[    14.385] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    14.385] (II) LoadModule: "ati"
[    14.385] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.385] (II) Module ati: vendor="X.Org Foundation"
[    14.385]     compiled for 1.10.0, module version = 6.14.0
[    14.385]     Module class: X.Org Video Driver
[    14.385]     ABI class: X.Org Video Driver, version 10.0
[    14.385] (II) LoadModule: "radeon"
[    14.386] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.386] (II) Module radeon: vendor="X.Org Foundation"
[    14.387]     compiled for 1.10.0, module version = 6.14.0
[    14.387]     Module class: X.Org Video Driver
[    14.387]     ABI class: X.Org Video Driver, version 10.0
[    14.387] (II) LoadModule: "vesa"
[    14.387] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.387] (II) Module vesa: vendor="X.Org Foundation"
[    14.387]     compiled for 1.10.0, module version = 2.3.0
[    14.387]     Module class: X.Org Video Driver
[    14.387]     ABI class: X.Org Video Driver, version 10.0
[    14.387] (II) LoadModule: "fbdev"
[    14.388] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.388] (II) Module fbdev: vendor="X.Org Foundation"
[    14.388]     compiled for 1.10.0, module version = 0.4.2
[    14.388]     ABI class: X.Org Video Driver, version 10.0
[    14.388] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
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
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS,
    Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS
[    14.412] (II) VESA: driver for VESA chipsets: vesa
[    14.412] (II) FBDEV: driver for framebuffer: fbdev
[    14.412] (++) using VT number 7

[    14.412] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.412] (II) [KMS] Kernel modesetting enabled.
[    14.412] (WW) Falling back to old probe method for vesa
[    14.412] (WW) Falling back to old probe method for fbdev
[    14.413] (II) Loading sub module "fbdevhw"
[    14.413] (II) LoadModule: "fbdevhw"
[    14.413] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.413] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.413]     compiled for 1.10.1, module version = 0.0.2
[    14.413]     ABI class: X.Org Video Driver, version 10.0
[    14.414] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.414] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    14.414] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.414] (==) RADEON(0): Default visual is TrueColor
[    14.414] (==) RADEON(0): RGB weight 888
[    14.414] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    14.414] (--) RADEON(0): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
[    14.414] (II) RADEON(0): PCIE card detected
[    14.414] drmOpenDevice: node name is /dev/dri/card0
[    14.414] drmOpenDevice: open result is 9, (OK)
[    14.414] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    14.414] drmOpenDevice: node name is /dev/dri/card0
[    14.414] drmOpenDevice: open result is 9, (OK)
[    14.414] drmOpenByBusid: drmOpenMinor returns 9
[    14.414] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    14.414] (II) RADEON(0): KMS Color Tiling: enabled
[    14.414] (II) RADEON(0): KMS Pageflipping: enabled
[    14.415] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    14.475] (II) RADEON(0): Output VGA-0 has no monitor section
[    14.499] (II) RADEON(0): Output DVI-0 has no monitor section
[    14.541] (II) RADEON(0): Output S-video has no monitor section
[    14.597] (II) RADEON(0): EDID for output VGA-0
[    14.597] (II) RADEON(0): Manufacturer: DEL  Model: 700e  Serial#: 0
[    14.597] (II) RADEON(0): Year: 2005  Week: 25
[    14.597] (II) RADEON(0): EDID Version: 1.3
[    14.597] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    14.597] (II) RADEON(0): Sync:  Separate
[    14.597] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    14.597] (II) RADEON(0): Gamma: 2.20
[    14.597] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    14.597] (II) RADEON(0): Default color space is primary color space
[    14.597] (II) RADEON(0): First detailed timing is preferred mode
[    14.598] (II) RADEON(0): redX: 0.636 redY: 0.348   greenX: 0.298 greenY: 0.615
[    14.598] (II) RADEON(0): blueX: 0.142 blueY: 0.072   whiteX: 0.313 whiteY: 0.329
[    14.598] (II) RADEON(0): Supported established timings:
[    14.598] (II) RADEON(0): 720x400@70Hz
[    14.598] (II) RADEON(0): 640x480@60Hz
[    14.598] (II) RADEON(0): 640x480@75Hz
[    14.598] (II) RADEON(0): 800x600@60Hz
[    14.598] (II) RADEON(0): 800x600@75Hz
[    14.598] (II) RADEON(0): 1024x768@60Hz
[    14.598] (II) RADEON(0): 1024x768@75Hz
[    14.598] (II) RADEON(0): 1280x1024@75Hz
[    14.598] (II) RADEON(0): Manufacturer's mask: 0
[    14.598] (II) RADEON(0): Supported standard timings:
[    14.598] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    14.598] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    14.598] (II) RADEON(0): Supported detailed timing:
[    14.598] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    14.598] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    14.598] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    14.598] (II) RADEON(0): Serial No: G656656PL6CU
[    14.598] (II) RADEON(0): Monitor name: Dell E193FP
[    14.598] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    14.598] (II) RADEON(0): EDID (in hex):
[    14.598] (II) RADEON(0):     00ffffffffffff0010ac0e7000000000
[    14.598] (II) RADEON(0):     190f010368261e782ec665a2594c9d24
[    14.598] (II) RADEON(0):     125054a54b00714f8180010101010101
[    14.598] (II) RADEON(0):     010101010101302a009851002a403070
[    14.598] (II) RADEON(0):     1300520e1100001e000000ff00473635
[    14.598] (II) RADEON(0):     36363536504c3643550a000000fc0044
[    14.598] (II) RADEON(0):     656c6c204531393346500a20000000fd
[    14.598] (II) RADEON(0):     00384c1e530e000a20202020202000b4
[    14.598] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    14.599] (II) RADEON(0): Using EDID range info for horizontal sync
[    14.599] (II) RADEON(0): Using EDID range info for vertical refresh
[    14.599] (II) RADEON(0): Printing DDC gathered Modelines:
[    14.599] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.599] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.599] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.599] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.599] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.599] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.599] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.599] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.599] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.599] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.599] (II) RADEON(0): Printing probed modes for output VGA-0
[    14.599] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.599] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.599] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.599] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    14.599] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.599] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.599] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.599] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.599] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.599] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.623] (II) RADEON(0): EDID for output DVI-0
[    14.643] (II) RADEON(0): EDID for output S-video
[    14.643] (II) RADEON(0): Output VGA-0 connected
[    14.643] (II) RADEON(0): Output DVI-0 disconnected
[    14.643] (II) RADEON(0): Output S-video disconnected
[    14.643] (II) RADEON(0): Using exact sizes for initial modes
[    14.643] (II) RADEON(0): Output VGA-0 using initial mode 1280x1024
[    14.643] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.643] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7ac0000
[    14.643] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    14.643] (**) RADEON(0): Display dimensions: (380, 300) mm
[    14.643] (**) RADEON(0): DPI set to (85, 86)
[    14.643] (II) Loading sub module "fb"
[    14.643] (II) LoadModule: "fb"
[    14.644] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.662] (II) Module fb: vendor="X.Org Foundation"
[    14.662]     compiled for 1.10.1, module version = 1.0.0
[    14.662]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.662] (II) Loading sub module "ramdac"
[    14.662] (II) LoadModule: "ramdac"
[    14.662] (II) Module "ramdac" already built-in
[    14.662] (II) Loading sub module "exa"
[    14.662] (II) LoadModule: "exa"
[    14.663] (II) Loading /usr/lib/xorg/modules/libexa.so
[    14.664] (II) Module exa: vendor="X.Org Foundation"
[    14.664]     compiled for 1.10.1, module version = 2.5.0
[    14.664]     ABI class: X.Org Video Driver, version 10.0
[    14.664] (II) UnloadModule: "vesa"
[    14.664] (II) Unloading vesa
[    14.664] (II) UnloadModule: "fbdev"
[    14.664] (II) Unloading fbdev
[    14.664] (II) UnloadModule: "fbdevhw"
[    14.664] (II) Unloading fbdevhw
[    14.664] (--) Depth 24 pixmap format is 32 bpp
[    14.664] (II) RADEON(0): [DRI2] Setup complete
[    14.664] (II) RADEON(0): [DRI2]   DRI driver: r300
[    14.665] (II) RADEON(0): Front buffer size: 5120K
[    14.665] (II) RADEON(0): VRAM usage limit set to 108518K
[    14.665] (==) RADEON(0): Backing store disabled
[    14.665] (II) RADEON(0): Direct rendering enabled
[    14.665] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    14.665] (II) RADEON(0): Setting EXA maxPitchBytes
[    14.665] (II) EXA(0): Driver allocated offscreen pixmaps
[    14.665] (II) EXA(0): Driver registered support for the following operations:
[    14.665] (II)         Solid
[    14.665] (II)         Copy
[    14.665] (II)         Composite (RENDER acceleration)
[    14.665] (II)         UploadToScreen
[    14.665] (II)         DownloadFromScreen
[    14.665] (II) RADEON(0): Acceleration enabled
[    14.665] (==) RADEON(0): DPMS enabled
[    14.665] (==) RADEON(0): Silken mouse enabled
[    14.666] (II) RADEON(0): Set up textured video
[    14.666] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.666] (--) RandR disabled
[    14.666] (II) Initializing built-in extension Generic Event Extension
[    14.666] (II) Initializing built-in extension SHAPE
[    14.666] (II) Initializing built-in extension MIT-SHM
[    14.666] (II) Initializing built-in extension XInputExtension
[    14.666] (II) Initializing built-in extension XTEST
[    14.667] (II) Initializing built-in extension BIG-REQUESTS
[    14.667] (II) Initializing built-in extension SYNC
[    14.667] (II) Initializing built-in extension XKEYBOARD
[    14.667] (II) Initializing built-in extension XC-MISC
[    14.667] (II) Initializing built-in extension SECURITY
[    14.667] (II) Initializing built-in extension XINERAMA
[    14.667] (II) Initializing built-in extension XFIXES
[    14.667] (II) Initializing built-in extension RENDER
[    14.667] (II) Initializing built-in extension RANDR
[    14.667] (II) Initializing built-in extension COMPOSITE
[    14.667] (II) Initializing built-in extension DAMAGE
[    14.667] (II) Initializing built-in extension GESTURE
[    14.683] (II) AIGLX: Trying DRI driver /usr/lib/dri/r300_dri.so
[    14.709] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.709] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.709] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.709] (II) AIGLX: enabled GLX_SGI_make_current_read
[    14.709] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.709] (II) AIGLX: Loaded and initialized r300
[    14.709] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.710] (II) RADEON(0): Setting screen physical size to 338 x 270
[    14.724] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.746] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.768] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.768] (II) LoadModule: "evdev"
[    14.769] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.769] (II) Module evdev: vendor="X.Org Foundation"
[    14.769]     compiled for 1.10.0.902, module version = 2.6.0
[    14.769]     Module class: X.Org XInput Driver
[    14.769]     ABI class: X.Org XInput driver, version 12.3
[    14.769] (II) Using input driver 'evdev' for 'Power Button'
[    14.769] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.770] (**) Power Button: always reports core events
[    14.770] (**) Power Button: Device: "/dev/input/event1"
[    14.780] (--) Power Button: Found keys
[    14.780] (II) Power Button: Configuring as keyboard
[    14.780] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.780] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.780] (**) Option "xkb_rules" "evdev"
[    14.780] (**) Option "xkb_model" "pc105"
[    14.780] (**) Option "xkb_layout" "us"
[    14.782] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.782] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.783] (II) Using input driver 'evdev' for 'Power Button'
[    14.783] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.783] (**) Power Button: always reports core events
[    14.783] (**) Power Button: Device: "/dev/input/event0"
[    14.796] (--) Power Button: Found keys
[    14.796] (II) Power Button: Configuring as keyboard
[    14.796] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.796] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.796] (**) Option "xkb_rules" "evdev"
[    14.796] (**) Option "xkb_model" "pc105"
[    14.796] (**) Option "xkb_layout" "us"
[    14.799] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event10)
[    14.799] (II) No input driver/identifier specified (ignoring)
[    14.799] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event4)
[    14.799] (II) No input driver/identifier specified (ignoring)
[    14.800] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event5)
[    14.800] (II) No input driver/identifier specified (ignoring)
[    14.800] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event6)
[    14.800] (II) No input driver/identifier specified (ignoring)
[    14.801] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event7)
[    14.801] (II) No input driver/identifier specified (ignoring)
[    14.801] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8)
[    14.801] (II) No input driver/identifier specified (ignoring)
[    14.802] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9)
[    14.802] (II) No input driver/identifier specified (ignoring)
[    14.804] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event2)
[    14.804] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[    14.804] (II) Using input driver 'evdev' for 'Logitech Optical USB Mouse'
[    14.804] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.804] (**) Logitech Optical USB Mouse: always reports core events
[    14.804] (**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
[    14.828] (--) Logitech Optical USB Mouse: Found 3 mouse buttons
[    14.828] (--) Logitech Optical USB Mouse: Found scroll wheel(s)
[    14.828] (--) Logitech Optical USB Mouse: Found relative axes
[    14.828] (--) Logitech Optical USB Mouse: Found x and y relative axes
[    14.828] (II) Logitech Optical USB Mouse: Configuring as mouse
[    14.828] (II) Logitech Optical USB Mouse: Adding scrollwheel support
[    14.828] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[    14.828] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.828] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2"
[    14.829] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[    14.829] (II) Logitech Optical USB Mouse: initialized for relative axes.
[    14.829] (**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
[    14.829] (**) Logitech Optical USB Mouse: (accel) acceleration profile 0
[    14.829] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[    14.829] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[    14.829] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[    14.829] (II) No input driver/identifier specified (ignoring)
[    14.830] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event3)
[    14.830] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.830] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    14.830] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.830] (**) Dell Dell USB Keyboard: always reports core events
[    14.831] (**) Dell Dell USB Keyboard: Device: "/dev/input/event3"
[    14.831] (--) Dell Dell USB Keyboard: Found keys
[    14.831] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    14.831] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3/event3"
[    14.831] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    14.831] (**) Option "xkb_rules" "evdev"
[    14.831] (**) Option "xkb_model" "pc105"
[    14.831] (**) Option "xkb_layout" "us"
[    16.869] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    16.869] (II) RADEON(0): Using hsync ranges from config file
[    16.869] (II) RADEON(0): Using vrefresh ranges from config file
[    16.869] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.869] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    16.869] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    16.869] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    16.869] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    16.869] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    16.869] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    16.869] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    16.869] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    16.869] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    16.869] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    17.015] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    17.015] (II) RADEON(0): Using hsync ranges from config file
[    17.015] (II) RADEON(0): Using vrefresh ranges from config file
[    17.016] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.016] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.016] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.016] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.016] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.016] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.016] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.016] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.016] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.016] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.016] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    17.121] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    17.121] (II) RADEON(0): Using hsync ranges from config file
[    17.121] (II) RADEON(0): Using vrefresh ranges from config file
[    17.121] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.121] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.121] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.121] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.121] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.121] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.121] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.121] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.121] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.121] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.121] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    17.970] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    17.970] (II) RADEON(0): Using hsync ranges from config file
[    17.970] (II) RADEON(0): Using vrefresh ranges from config file
[    17.970] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.970] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.970] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.970] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.970] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.970] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.970] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.970] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.970] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.970] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.970] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.075] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[    24.075] (II) RADEON(0): Using hsync ranges from config file
[    24.075] (II) RADEON(0): Using vrefresh ranges from config file
[    24.075] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.079] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.079] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.079] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.079] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.079] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.079] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.079] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.079] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.079] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.079] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1681.237] (II) RADEON(0): EDID vendor "DEL", prod id 28686
[  1681.237] (II) RADEON(0): Using hsync ranges from config file
[  1681.237] (II) RADEON(0): Using vrefresh ranges from config file
[  1681.237] (II) RADEON(0): Printing DDC gathered Modelines:
[  1681.237] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1681.237] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1681.237] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1681.237] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1681.237] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1681.237] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1681.238] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1681.238] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1681.238] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1681.238] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)

---

### Post by papibe on 2011-08-20
It looks that the monitor information is read correctly. I took the hex information below the line: 'EDID (in hex):' and converted to a binary. Then I used parse-edid (from the read-edid package).

This is what I got:
```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	Identifier "Dell E193FP"
	VendorName "DEL"
	ModelName "Dell E193FP"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 140 MHz
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection
```
Is that correct?
Is that your model, resolution and timings? (check your manual).

Regards.

EDIT: My Dell monitor has a menu button that allow me to do a 'Factory Reset'. At this point it sounds like a reasonable test.

---

### Post by sffuji on 2011-08-20
Yes, I was able to fix the settings on the Monitor display, and now it doesn't "bleed" off the screen.  However, this helped me to discover that the repair person who "resurrected" my Dell Dimension 9100 had installed the client Ubuntu version, not the server version, so in order to fix one of my other threads (sharing the installed printer to the wireless network), I'll need to install the server version without disrupting the currently non-functional Win-XP partition.  

Thanks!!:)

---

### Post by Stray Wolf on 2011-09-25
Hope this is in the right thread...

I updated my video card to an EVGA Nvidia GeForce GT 520 and found I had to run 11.04 for newer drivers.  The screen was too small (1 inch black on each side) on 10.04 and Nvidia x-server settings wasn't loading.  Now on Natty (11.04 right?) the screen is too big and Nvidia x-server settings loads but I can't find how to shrink the screen size.  The settings gui seems to shrink or grow in the window depending on what "tab" on the left I set and no scroll bar appears when that tabs settings (on the right) are lower than the window and off-screen.  Is there a manual way to force screen size to maybe be a half inch smaller all around?

---

### Post by BushyIII on 2011-10-06
> **papibe said:**
> It looks that the monitor information is read correctly. I took the hex information below the line: 'EDID (in hex):' and converted to a binary. Then I used parse-edid (from the read-edid package).

This is what I got:
```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	Identifier "Dell E193FP"
	VendorName "DEL"
	ModelName "Dell E193FP"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 140 MHz
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection
```
Is that correct?
Is that your model, resolution and timings? (check your manual).

Regards.

EDIT: My Dell monitor has a menu button that allow me to do a 'Factory Reset'. At this point it sounds like a reasonable test.
 I have the same problem using HDMI to a hdtv.  How do I solve the problem?

---

### Post by papibe on 2011-10-06
Hi BushyIII, I would suggest you to create a new thread to take care of your concern. Include more information like your Ubuntu version, graphic card, TV brand and model, etc.

Regards.

---

### Post by BushyIII on 2011-10-07
> **papibe said:**
> Hi BushyIII, I would suggest you to create a new thread to take care of your concern. Include more information like your Ubuntu version, graphic card, TV brand and model, etc.

Regards.


Will do, thanks for the advice

---

