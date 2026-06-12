---
title: "Wrong colour depth with open source radeon driver"
date: 2014-03-30
forum: Multimedia Software
---

### Post by parashep on 2014-03-30
I switched from the ATI Catalyst driver to the open source radeon driver because fglrx was no good. the open source driver is way faster, but my monitor's colour depth is off. I'm not sure what it's displaying as but there's definitely visible gradient banding. I've searched online a bit, but haven't found an up-to-date solution. the drivers are supposed to detect my card and configure things automatically... my card is Mobility Radeon HD 5870. I have no Xorg.conf.

---

### Post by Yellow Pasque on 2014-03-31
Can you post the /var/log/Xorg.0.log file? Use code tags..

---

### Post by parashep on 2014-03-31
here it is! I haven't taken a look at it myself but I will in just a moment.
EDIT: I noticed it does say using 8 bits per channel as the driver initializes, but when it's detecting the monitor it says: "[    25.325] (II) RADEON(0): 6 bits per channel". I wonder why?
```
[    24.811] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    24.811] X Protocol Version 11, Revision 0
[    24.811] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    24.811] Current Operating System: Linux fleece-ubuntu 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64
[    24.811] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=cf7fe229-6aa3-422a-86aa-06601097874c ro quiet splash radeon.dpm=1 vt.handoff=7
[    24.811] Build Date: 17 December 2013  10:06:15AM
[    24.811] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    24.811] Current version of pixman: 0.30.2
[    24.811]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.811] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.811] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 30 20:06:45 2014
[    24.927] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.927] (==) No Layout section.  Using the first Screen section.
[    24.927] (==) No screen section available. Using defaults.
[    24.927] (**) |-->Screen "Default Screen Section" (0)
[    24.927] (**) |   |-->Monitor "<default monitor>"
[    24.927] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.927] (==) Automatically adding devices
[    24.927] (==) Automatically enabling devices
[    24.927] (==) Automatically adding GPU devices
[    24.927] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.927]     Entry deleted from font path.
[    24.927] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.927]     Entry deleted from font path.
[    24.927] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.927]     Entry deleted from font path.
[    24.927] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.927]     Entry deleted from font path.
[    24.927] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.927]     Entry deleted from font path.
[    24.927] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.927] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.927] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.927] (II) Loader magic: 0x7f74ca860d20
[    24.927] (II) Module ABI versions:
[    24.927]     X.Org ANSI C Emulation: 0.4
[    24.927]     X.Org Video Driver: 14.1
[    24.927]     X.Org XInput driver : 19.1
[    24.927]     X.Org Server Extension : 7.0
[    24.927] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.929] (--) PCI:*(0:1:0:0) 1002:68a1:103c:1590 rev 0, Mem @ 0xc0000000/268435456, 0xd6000000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[    24.929] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.929] Initializing built-in extension Generic Event Extension
[    24.929] Initializing built-in extension SHAPE
[    24.929] Initializing built-in extension MIT-SHM
[    24.929] Initializing built-in extension XInputExtension
[    24.929] Initializing built-in extension XTEST
[    24.929] Initializing built-in extension BIG-REQUESTS
[    24.929] Initializing built-in extension SYNC
[    24.929] Initializing built-in extension XKEYBOARD
[    24.929] Initializing built-in extension XC-MISC
[    24.929] Initializing built-in extension SECURITY
[    24.929] Initializing built-in extension XINERAMA
[    24.929] Initializing built-in extension XFIXES
[    24.929] Initializing built-in extension RENDER
[    24.929] Initializing built-in extension RANDR
[    24.929] Initializing built-in extension COMPOSITE
[    24.929] Initializing built-in extension DAMAGE
[    24.929] Initializing built-in extension MIT-SCREEN-SAVER
[    24.929] Initializing built-in extension DOUBLE-BUFFER
[    24.929] Initializing built-in extension RECORD
[    24.929] Initializing built-in extension DPMS
[    24.929] Initializing built-in extension X-Resource
[    24.929] Initializing built-in extension XVideo
[    24.929] Initializing built-in extension XVideo-MotionCompensation
[    24.929] Initializing built-in extension SELinux
[    24.929] Initializing built-in extension XFree86-VidModeExtension
[    24.929] Initializing built-in extension XFree86-DGA
[    24.929] Initializing built-in extension XFree86-DRI
[    24.929] Initializing built-in extension DRI2
[    24.930] (II) "glx" will be loaded by default.
[    24.930] (WW) "xmir" is not to be loaded by default. Skipping.
[    24.930] (II) LoadModule: "dri2"
[    24.930] (II) Module "dri2" already built-in
[    24.930] (II) LoadModule: "glamoregl"
[    24.951] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    25.189] (II) Module glamoregl: vendor="X.Org Foundation"
[    25.189]     compiled for 1.14.5, module version = 0.6.0
[    25.189]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.189] (II) LoadModule: "glx"
[    25.189] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.189] (II) Module glx: vendor="X.Org Foundation"
[    25.189]     compiled for 1.14.5, module version = 1.0.0
[    25.189]     ABI class: X.Org Server Extension, version 7.0
[    25.189] (==) AIGLX enabled
[    25.189] Loading extension GLX
[    25.189] (==) Matched fglrx as autoconfigured driver 0
[    25.189] (==) Matched ati as autoconfigured driver 1
[    25.189] (==) Matched fglrx as autoconfigured driver 2
[    25.189] (==) Matched ati as autoconfigured driver 3
[    25.189] (==) Matched vesa as autoconfigured driver 4
[    25.189] (==) Matched modesetting as autoconfigured driver 5
[    25.189] (==) Matched fbdev as autoconfigured driver 6
[    25.189] (==) Assigned the driver to the xf86ConfigLayout
[    25.189] (II) LoadModule: "fglrx"
[    25.197] (WW) Warning, couldn't open module fglrx
[    25.197] (II) UnloadModule: "fglrx"
[    25.197] (II) Unloading fglrx
[    25.197] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    25.197] (II) LoadModule: "ati"
[    25.197] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    25.197] (II) Module ati: vendor="X.Org Foundation"
[    25.197]     compiled for 1.14.5, module version = 7.3.99
[    25.197]     Module class: X.Org Video Driver
[    25.197]     ABI class: X.Org Video Driver, version 14.1
[    25.197] (II) LoadModule: "radeon"
[    25.197] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    25.221] (II) Module radeon: vendor="X.Org Foundation"
[    25.221]     compiled for 1.14.5, module version = 7.3.99
[    25.221]     Module class: X.Org Video Driver
[    25.221]     ABI class: X.Org Video Driver, version 14.1
[    25.221] (II) LoadModule: "vesa"
[    25.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.222] (II) Module vesa: vendor="X.Org Foundation"
[    25.222]     compiled for 1.14.1, module version = 2.3.2
[    25.222]     Module class: X.Org Video Driver
[    25.222]     ABI class: X.Org Video Driver, version 14.1
[    25.222] (II) LoadModule: "modesetting"
[    25.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.222] (II) Module modesetting: vendor="X.Org Foundation"
[    25.222]     compiled for 1.14.1, module version = 0.8.0
[    25.222]     Module class: X.Org Video Driver
[    25.222]     ABI class: X.Org Video Driver, version 14.1
[    25.222] (II) LoadModule: "fbdev"
[    25.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.222] (II) Module fbdev: vendor="X.Org Foundation"
[    25.222]     compiled for 1.14.1, module version = 0.4.3
[    25.222]     Module class: X.Org Video Driver
[    25.222]     ABI class: X.Org Video Driver, version 14.1
[    25.222] (==) Matched fglrx as autoconfigured driver 0
[    25.222] (==) Matched ati as autoconfigured driver 1
[    25.222] (==) Matched fglrx as autoconfigured driver 2
[    25.222] (==) Matched ati as autoconfigured driver 3
[    25.222] (==) Matched vesa as autoconfigured driver 4
[    25.222] (==) Matched modesetting as autoconfigured driver 5
[    25.222] (==) Matched fbdev as autoconfigured driver 6
[    25.222] (==) Assigned the driver to the xf86ConfigLayout
[    25.222] (II) LoadModule: "fglrx"
[    25.223] (WW) Warning, couldn't open module fglrx
[    25.223] (II) UnloadModule: "fglrx"
[    25.223] (II) Unloading fglrx
[    25.223] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    25.223] (II) LoadModule: "ati"
[    25.223] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    25.223] (II) Module ati: vendor="X.Org Foundation"
[    25.223]     compiled for 1.14.5, module version = 7.3.99
[    25.223]     Module class: X.Org Video Driver
[    25.223]     ABI class: X.Org Video Driver, version 14.1
[    25.223] (II) LoadModule: "vesa"
[    25.223] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.223] (II) Module vesa: vendor="X.Org Foundation"
[    25.223]     compiled for 1.14.1, module version = 2.3.2
[    25.223]     Module class: X.Org Video Driver
[    25.223]     ABI class: X.Org Video Driver, version 14.1
[    25.223] (II) UnloadModule: "vesa"
[    25.223] (II) Unloading vesa
[    25.223] (II) Failed to load module "vesa" (already loaded, 0)
[    25.223] (II) LoadModule: "modesetting"
[    25.223] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.223] (II) Module modesetting: vendor="X.Org Foundation"
[    25.223]     compiled for 1.14.1, module version = 0.8.0
[    25.223]     Module class: X.Org Video Driver
[    25.223]     ABI class: X.Org Video Driver, version 14.1
[    25.223] (II) UnloadModule: "modesetting"
[    25.223] (II) Unloading modesetting
[    25.223] (II) Failed to load module "modesetting" (already loaded, 0)
[    25.223] (II) LoadModule: "fbdev"
[    25.223] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.223] (II) Module fbdev: vendor="X.Org Foundation"
[    25.223]     compiled for 1.14.1, module version = 0.4.3
[    25.223]     Module class: X.Org Video Driver
[    25.223]     ABI class: X.Org Video Driver, version 14.1
[    25.223] (II) UnloadModule: "fbdev"
[    25.223] (II) Unloading fbdev
[    25.223] (II) Failed to load module "fbdev" (already loaded, 0)
[    25.223] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
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
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    25.230] (II) VESA: driver for VESA chipsets: vesa
[    25.230] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.230] (II) FBDEV: driver for framebuffer: fbdev
[    25.230] (++) using VT number 7

[    25.230] (II) [KMS] Kernel modesetting enabled.
[    25.230] (WW) Falling back to old probe method for vesa
[    25.230] (WW) Falling back to old probe method for modesetting
[    25.230] (WW) Falling back to old probe method for fbdev
[    25.230] (II) Loading sub module "fbdevhw"
[    25.230] (II) LoadModule: "fbdevhw"
[    25.230] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.230] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.230]     compiled for 1.14.5, module version = 0.0.2
[    25.230]     ABI class: X.Org Video Driver, version 14.1
[    25.231] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.231] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    25.231] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    25.231] (==) RADEON(0): Default visual is TrueColor
[    25.231] (==) RADEON(0): RGB weight 888
[    25.231] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    25.231] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5800 Series" (ChipID = 0x68a1)
[    25.231] (II) Loading sub module "dri2"
[    25.231] (II) LoadModule: "dri2"
[    25.231] (II) Module "dri2" already built-in
[    25.231] (II) Loading sub module "exa"
[    25.231] (II) LoadModule: "exa"
[    25.231] (II) Loading /usr/lib/xorg/modules/libexa.so
[    25.231] (II) Module exa: vendor="X.Org Foundation"
[    25.231]     compiled for 1.14.5, module version = 2.6.0
[    25.231]     ABI class: X.Org Video Driver, version 14.1
[    25.231] (II) RADEON(0): KMS Color Tiling: enabled
[    25.231] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    25.231] (II) RADEON(0): KMS Pageflipping: enabled
[    25.231] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    25.256] (II) RADEON(0): Output eDP has no monitor section
[    25.272] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[    25.274] (II) RADEON(0): Output HDMI-0 has no monitor section
[    25.300] (II) RADEON(0): Output VGA-0 has no monitor section
[    25.325] (II) RADEON(0): EDID for output eDP
[    25.325] (II) RADEON(0): Manufacturer: LGD  Model: 2c4  Serial#: 0
[    25.325] (II) RADEON(0): Year: 2010  Week: 0
[    25.325] (II) RADEON(0): EDID Version: 1.4
[    25.325] (II) RADEON(0): Digital Display Input
[    25.325] (II) RADEON(0): 6 bits per channel
[    25.325] (II) RADEON(0): Digital interface is DisplayPort
[    25.325] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    25.325] (II) RADEON(0): Gamma: 2.20
[    25.325] (II) RADEON(0): No DPMS capabilities specified
[    25.325] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[    25.325] (II) RADEON(0): First detailed timing is preferred mode
[    25.325] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[    25.325] (II) RADEON(0): redX: 0.642 redY: 0.345   greenX: 0.339 greenY: 0.620
[    25.325] (II) RADEON(0): blueX: 0.148 blueY: 0.062   whiteX: 0.313 whiteY: 0.329
[    25.325] (II) RADEON(0): Manufacturer's mask: 0
[    25.325] (II) RADEON(0): Supported detailed timing:
[    25.325] (II) RADEON(0): clock: 148.5 MHz   Image Size:  382 x 215 mm
[    25.325] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    25.325] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    25.325] (II) RADEON(0): Supported detailed timing:
[    25.325] (II) RADEON(0): clock: 392.2 MHz   Image Size:  382 x 215 mm
[    25.325] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    25.325] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1964 v_border: 0
[    25.325] (II) RADEON(0): Supported detailed timing:
[    25.325] (II) RADEON(0): clock: 396.4 MHz   Image Size:  382 x 215 mm
[    25.325] (II) RADEON(0): h_active: 1920  h_sync: 1940  h_sync_end 1960 h_blank_end 2080 h_border: 0
[    25.325] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1588 v_border: 0
[    25.325] (II) RADEON(0):  LP173WF2-TPB1
[    25.325] (II) RADEON(0): EDID (in hex):
[    25.325] (II) RADEON(0):     00ffffffffffff0030e4c40200000000
[    25.325] (II) RADEON(0):     0014010495261578025f35a458569e26
[    25.325] (II) RADEON(0):     0f505400000001010101010101010101
[    25.325] (II) RADEON(0):     010101010101023a801871382d40582c
[    25.325] (II) RADEON(0):     45007ed710000019319980a070387443
[    25.325] (II) RADEON(0):     302035007ed710000019d39a80a07038
[    25.325] (II) RADEON(0):     fc41141435007ed710000019000000fe
[    25.325] (II) RADEON(0):     004c503137335746322d54504231004a
[    25.325] (II) RADEON(0): Printing probed modes for output eDP
[    25.325] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    25.325] (II) RADEON(0): Modeline "1920x1080"x120.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    25.325] (II) RADEON(0): Modeline "1920x1080"x96.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    25.325] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.325] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    25.325] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[    25.325] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.325] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[    25.325] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    25.325] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    25.325] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    25.325] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.325] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    25.325] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    25.325] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    25.325] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    25.325] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    25.340] (II) RADEON(0): EDID for output DisplayPort-0
[    25.342] (II) RADEON(0): EDID for output HDMI-0
[    25.368] (II) RADEON(0): EDID for output VGA-0
[    25.368] (II) RADEON(0): Output eDP connected
[    25.368] (II) RADEON(0): Output DisplayPort-0 disconnected
[    25.368] (II) RADEON(0): Output HDMI-0 disconnected
[    25.368] (II) RADEON(0): Output VGA-0 disconnected
[    25.368] (II) RADEON(0): Using exact sizes for initial modes
[    25.368] (II) RADEON(0): Output eDP using initial mode 1920x1080
[    25.368] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.368] (II) RADEON(0): mem size init: gart size :1fdee000 vram size: s:40000000 visible:3f7d7000
[    25.368] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    25.368] (==) RADEON(0): DPI set to (96, 96)
[    25.368] (II) Loading sub module "fb"
[    25.368] (II) LoadModule: "fb"
[    25.368] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.368] (II) Module fb: vendor="X.Org Foundation"
[    25.368]     compiled for 1.14.5, module version = 1.0.0
[    25.368]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.368] (II) Loading sub module "ramdac"
[    25.368] (II) LoadModule: "ramdac"
[    25.368] (II) Module "ramdac" already built-in
[    25.368] (II) UnloadModule: "vesa"
[    25.368] (II) Unloading vesa
[    25.368] (II) UnloadModule: "modesetting"
[    25.368] (II) Unloading modesetting
[    25.369] (II) UnloadModule: "fbdev"
[    25.369] (II) Unloading fbdev
[    25.369] (II) UnloadSubModule: "fbdevhw"
[    25.369] (II) Unloading fbdevhw
[    25.369] (--) Depth 24 pixmap format is 32 bpp
[    25.369] (II) RADEON(0): [DRI2] Setup complete
[    25.369] (II) RADEON(0): [DRI2]   DRI driver: r600
[    25.369] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    25.369] (II) RADEON(0): Front buffer size: 8640K
[    25.369] (II) RADEON(0): VRAM usage limit set to 928335K
[    25.369] (==) RADEON(0): Backing store disabled
[    25.369] (II) RADEON(0): Direct rendering enabled
[    25.369] (II) EXA(0): Driver allocated offscreen pixmaps
[    25.369] (II) EXA(0): Driver registered support for the following operations:
[    25.369] (II)         Solid
[    25.369] (II)         Copy
[    25.369] (II)         Composite (RENDER acceleration)
[    25.369] (II)         UploadToScreen
[    25.369] (II)         DownloadFromScreen
[    25.369] (II) RADEON(0): Acceleration enabled
[    25.369] (==) RADEON(0): DPMS enabled
[    25.369] (==) RADEON(0): Silken mouse enabled
[    25.369] (II) RADEON(0): Set up textured video
[    25.369] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    25.369] (II) RADEON(0): [XvMC] Extension initialized.
[    25.369] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.369] (--) RandR disabled
[    25.373] (II) SELinux: Disabled on system
[    25.988] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.988] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.988] (II) AIGLX: enabled GLX_ARB_create_context
[    25.988] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    25.988] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    25.988] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.988] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.989] (II) AIGLX: Loaded and initialized r600
[    25.989] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.288] (II) RADEON(0): Setting screen physical size to 508 x 285
[    27.297] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.298] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.298] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.298] (II) LoadModule: "evdev"
[    27.299] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.315] (II) Module evdev: vendor="X.Org Foundation"
[    27.315]     compiled for 1.14.1, module version = 2.7.3
[    27.315]     Module class: X.Org XInput Driver
[    27.315]     ABI class: X.Org XInput driver, version 19.1
[    27.315] (II) Using input driver 'evdev' for 'Power Button'
[    27.315] (**) Power Button: always reports core events
[    27.315] (**) evdev: Power Button: Device: "/dev/input/event2"
[    27.315] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.316] (--) evdev: Power Button: Found keys
[    27.316] (II) evdev: Power Button: Configuring as keyboard
[    27.316] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    27.316] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.316] (**) Option "xkb_rules" "evdev"
[    27.316] (**) Option "xkb_model" "pc105"
[    27.316] (**) Option "xkb_layout" "us"
[    27.316] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    27.316] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.316] (II) Using input driver 'evdev' for 'Video Bus'
[    27.316] (**) Video Bus: always reports core events
[    27.316] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    27.316] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.316] (--) evdev: Video Bus: Found keys
[    27.316] (II) evdev: Video Bus: Configuring as keyboard
[    27.316] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input5/event5"
[    27.316] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.316] (**) Option "xkb_rules" "evdev"
[    27.316] (**) Option "xkb_model" "pc105"
[    27.316] (**) Option "xkb_layout" "us"
[    27.317] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.317] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.317] (II) Using input driver 'evdev' for 'Power Button'
[    27.317] (**) Power Button: always reports core events
[    27.317] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.317] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.317] (--) evdev: Power Button: Found keys
[    27.317] (II) evdev: Power Button: Configuring as keyboard
[    27.317] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.317] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    27.317] (**) Option "xkb_rules" "evdev"
[    27.317] (**) Option "xkb_model" "pc105"
[    27.317] (**) Option "xkb_layout" "us"
[    27.317] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    27.317] (II) No input driver specified, ignoring this device.
[    27.317] (II) This device may have been added with another device file.
[    27.317] (II) config/udev: Adding drm device (/dev/dri/card0)
[    27.317] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.317] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event12)
[    27.317] (II) No input driver specified, ignoring this device.
[    27.317] (II) This device may have been added with another device file.
[    27.318] (II) config/udev: Adding input device HDA Intel MID Front Headphone (/dev/input/event7)
[    27.318] (II) No input driver specified, ignoring this device.
[    27.318] (II) This device may have been added with another device file.
[    27.318] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event8)
[    27.318] (II) No input driver specified, ignoring this device.
[    27.318] (II) This device may have been added with another device file.
[    27.318] (II) config/udev: Adding input device LITE-ON Technology USB NetVista Full Width Keyboard. (/dev/input/event4)
[    27.318] (**) LITE-ON Technology USB NetVista Full Width Keyboard.: Applying InputClass "evdev keyboard catchall"
[    27.318] (II) Using input driver 'evdev' for 'LITE-ON Technology USB NetVista Full Width Keyboard.'
[    27.318] (**) LITE-ON Technology USB NetVista Full Width Keyboard.: always reports core events
[    27.318] (**) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Device: "/dev/input/event4"
[    27.318] (--) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Vendor 0x4b3 Product 0x3025
[    27.318] (--) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Found keys
[    27.318] (II) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Configuring as keyboard
[    27.318] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/usb3/3-1/3-1:1.0/input/input4/event4"
[    27.318] (II) XINPUT: Adding extended input device "LITE-ON Technology USB NetVista Full Width Keyboard." (type: KEYBOARD, id 9)
[    27.318] (**) Option "xkb_rules" "evdev"
[    27.318] (**) Option "xkb_model" "pc105"
[    27.318] (**) Option "xkb_layout" "us"
[    27.319] (II) config/udev: Adding input device HP ENVY HD Webcam (/dev/input/event10)
[    27.319] (**) HP ENVY HD Webcam: Applying InputClass "evdev keyboard catchall"
[    27.319] (II) Using input driver 'evdev' for 'HP ENVY HD Webcam'
[    27.319] (**) HP ENVY HD Webcam: always reports core events
[    27.319] (**) evdev: HP ENVY HD Webcam: Device: "/dev/input/event10"
[    27.319] (--) evdev: HP ENVY HD Webcam: Vendor 0x408 Product 0x1af1
[    27.319] (--) evdev: HP ENVY HD Webcam: Found keys
[    27.319] (II) evdev: HP ENVY HD Webcam: Configuring as keyboard
[    27.319] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input10/event10"
[    27.319] (II) XINPUT: Adding extended input device "HP ENVY HD Webcam" (type: KEYBOARD, id 10)
[    27.319] (**) Option "xkb_rules" "evdev"
[    27.319] (**) Option "xkb_model" "pc105"
[    27.319] (**) Option "xkb_layout" "us"
[    27.319] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.319] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.319] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.319] (**) AT Translated Set 2 keyboard: always reports core events
[    27.319] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.319] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.319] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.319] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.319] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    27.319] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    27.319] (**) Option "xkb_rules" "evdev"
[    27.319] (**) Option "xkb_model" "pc105"
[    27.319] (**) Option "xkb_layout" "us"
[    27.320] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[    27.320] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.320] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.320] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    27.320] (II) LoadModule: "synaptics"
[    27.320] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.320] (II) Module synaptics: vendor="X.Org Foundation"
[    27.320]     compiled for 1.14.2, module version = 1.7.1
[    27.320]     Module class: X.Org XInput Driver
[    27.320]     ABI class: X.Org XInput driver, version 19.1
[    27.320] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.320] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.320] (**) Option "Device" "/dev/input/event11"
[    27.452] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    27.452] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5672 (res 46)
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4550 (res 61)
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    27.452] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    27.452] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.452] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.484] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    27.484] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    27.484] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.484] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    27.484] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    27.484] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.484] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.484] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.484] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.484] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.484] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.484] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.484] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    27.484] (II) No input driver specified, ignoring this device.
[    27.484] (II) This device may have been added with another device file.
[    27.485] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    27.485] (II) No input driver specified, ignoring this device.
[    27.485] (II) This device may have been added with another device file.
[    27.486] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event9)
[    27.486] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.486] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    27.486] (**) HP WMI hotkeys: always reports core events
[    27.486] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event9"
[    27.486] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    27.486] (--) evdev: HP WMI hotkeys: Found keys
[    27.486] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    27.486] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[    27.486] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    27.486] (**) Option "xkb_rules" "evdev"
[    27.486] (**) Option "xkb_model" "pc105"
[    27.486] (**) Option "xkb_layout" "us"
[    29.034] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    29.034] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.035] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    29.035] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    29.035] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    30.225] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    30.225] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.225] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    30.225] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    30.225] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    30.275] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.320] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.325] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.333] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    31.333] (II) RADEON(0): Printing DDC gathered Modelines:
[    31.333] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    31.333] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    31.333] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    31.374] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.589] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    31.848] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    34.835] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    45.989] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    45.989] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.989] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    45.989] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    45.989] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    47.981] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    47.982] (II) RADEON(0): Printing DDC gathered Modelines:
[    47.982] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    47.982] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    47.982] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    48.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.109] (II) RADEON(0): EDID vendor "LGD", prod id 708
[    48.109] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.109] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[    48.109] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[    48.109] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[    48.219] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    48.497] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    49.124] (II) XKB: reuse xkmfile /var/lib/xkb/server-979EE7C0CB4F7DD92E0D4C48F3277E929EB46CDC.xkm
[    51.238] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[   346.508] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/mouse1)
[   346.508] (II) No input driver specified, ignoring this device.
[   346.508] (II) This device may have been added with another device file.
[   346.508] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/event13)
[   346.508] (**) HP Bluetooth Laser Mobile Mouse: Applying InputClass "evdev pointer catchall"
[   346.508] (II) Using input driver 'evdev' for 'HP Bluetooth Laser Mobile Mouse'
[   346.509] (**) HP Bluetooth Laser Mobile Mouse: always reports core events
[   346.509] (**) evdev: HP Bluetooth Laser Mobile Mouse: Device: "/dev/input/event13"
[   346.509] (--) evdev: HP Bluetooth Laser Mobile Mouse: Vendor 0xd62 Product 0x558
[   346.509] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found 3 mouse buttons
[   346.509] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found scroll wheel(s)
[   346.509] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found relative axes
[   346.509] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found x and y relative axes
[   346.509] (II) evdev: HP Bluetooth Laser Mobile Mouse: Configuring as mouse
[   346.509] (II) evdev: HP Bluetooth Laser Mobile Mouse: Adding scrollwheel support
[   346.509] (**) evdev: HP Bluetooth Laser Mobile Mouse: YAxisMapping: buttons 4 and 5
[   346.509] (**) evdev: HP Bluetooth Laser Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   346.509] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/bluetooth/hci0/hci0:11/input13/event13"
[   346.509] (II) XINPUT: Adding extended input device "HP Bluetooth Laser Mobile Mouse" (type: MOUSE, id 14)
[   346.509] (II) evdev: HP Bluetooth Laser Mobile Mouse: initialized for relative axes.
[   346.510] (**) HP Bluetooth Laser Mobile Mouse: (accel) keeping acceleration scheme 1
[   346.510] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration profile 0
[   346.510] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration factor: 2.000
[   346.510] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration threshold: 4
[   688.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[   707.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3625.833] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3629.149] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3748.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3750.132] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3751.667] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3756.107] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3785.662] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  3809.941] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  4097.277] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  4143.840] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  4553.889] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  4553.889] (II) RADEON(0): Printing DDC gathered Modelines:
[  4553.889] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  4553.889] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  4553.889] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  4932.234] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  4932.234] (II) RADEON(0): Printing DDC gathered Modelines:
[  4932.234] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  4932.234] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  4932.234] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  5394.765] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  5394.765] (II) RADEON(0): Printing DDC gathered Modelines:
[  5394.765] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  5394.765] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  5394.766] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  5684.328] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  5702.792] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  5702.792] (II) RADEON(0): Printing DDC gathered Modelines:
[  5702.792] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  5702.792] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  5702.792] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  5789.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  7404.264] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  7533.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[  7536.392] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  7536.392] (II) RADEON(0): Printing DDC gathered Modelines:
[  7536.392] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  7536.392] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  7536.392] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  8792.404] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  8792.404] (II) RADEON(0): Printing DDC gathered Modelines:
[  8792.404] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  8792.404] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  8792.404] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  8792.469] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  8792.469] (II) RADEON(0): Printing DDC gathered Modelines:
[  8792.469] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  8792.469] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  8792.469] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  8792.783] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  8792.783] (II) RADEON(0): Printing DDC gathered Modelines:
[  8792.783] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  8792.784] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  8792.784] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9347.105] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9347.105] (II) RADEON(0): Printing DDC gathered Modelines:
[  9347.105] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9347.105] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9347.105] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9347.169] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9347.169] (II) RADEON(0): Printing DDC gathered Modelines:
[  9347.169] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9347.169] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9347.169] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9347.445] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9347.445] (II) RADEON(0): Printing DDC gathered Modelines:
[  9347.445] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9347.445] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9347.445] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9561.255] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9561.255] (II) RADEON(0): Printing DDC gathered Modelines:
[  9561.255] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9561.255] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9561.255] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9575.273] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9575.273] (II) RADEON(0): Printing DDC gathered Modelines:
[  9575.273] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9575.273] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9575.273] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.099] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.099] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.099] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.099] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.099] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.160] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.160] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.160] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.160] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.160] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.225] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.225] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.225] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.225] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.225] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.288] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.288] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.288] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.288] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.288] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.353] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.353] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.353] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.353] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.353] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.416] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.416] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.416] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.417] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.417] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.481] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.481] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.481] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.481] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.481] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9636.544] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9636.544] (II) RADEON(0): Printing DDC gathered Modelines:
[  9636.544] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9636.544] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9636.544] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.660] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.660] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.660] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.660] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.660] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.728] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.728] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.728] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.728] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.728] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.793] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.793] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.793] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.793] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.793] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.857] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.857] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.857] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.857] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.857] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.921] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.921] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.921] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.921] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.921] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9755.985] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9755.985] (II) RADEON(0): Printing DDC gathered Modelines:
[  9755.985] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9755.985] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9755.985] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9756.049] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9756.049] (II) RADEON(0): Printing DDC gathered Modelines:
[  9756.049] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9756.049] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9756.049] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9756.112] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9756.112] (II) RADEON(0): Printing DDC gathered Modelines:
[  9756.112] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9756.112] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9756.112] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.443] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.444] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.444] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.444] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.444] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.509] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.509] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.509] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.509] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.509] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.573] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.573] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.573] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.573] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.573] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.636] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.636] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.636] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.636] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.636] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.701] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.701] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.701] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.701] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.701] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.764] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.764] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.764] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.764] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.764] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.829] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.829] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.829] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.829] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.829] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9872.892] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9872.892] (II) RADEON(0): Printing DDC gathered Modelines:
[  9872.892] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9872.892] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9872.892] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9877.763] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9877.763] (II) RADEON(0): Printing DDC gathered Modelines:
[  9877.763] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9877.763] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9877.763] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9877.824] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9877.824] (II) RADEON(0): Printing DDC gathered Modelines:
[  9877.824] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9877.824] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9877.824] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9877.888] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9877.888] (II) RADEON(0): Printing DDC gathered Modelines:
[  9877.888] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9877.888] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9877.888] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9877.952] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9877.952] (II) RADEON(0): Printing DDC gathered Modelines:
[  9877.952] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9877.952] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9877.952] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9878.017] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9878.017] (II) RADEON(0): Printing DDC gathered Modelines:
[  9878.017] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9878.017] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9878.017] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9878.080] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9878.080] (II) RADEON(0): Printing DDC gathered Modelines:
[  9878.080] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9878.080] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9878.080] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9878.144] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9878.144] (II) RADEON(0): Printing DDC gathered Modelines:
[  9878.144] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9878.144] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9878.144] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[  9878.208] (II) RADEON(0): EDID vendor "LGD", prod id 708
[  9878.208] (II) RADEON(0): Printing DDC gathered Modelines:
[  9878.208] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[  9878.208] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[  9878.208] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.637] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.637] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.637] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.637] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.637] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.700] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.700] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.700] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.700] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.700] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.765] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.765] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.765] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.765] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.765] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.828] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.828] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.828] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.828] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.828] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.893] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.893] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.893] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.893] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.893] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10121.956] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10121.956] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10121.956] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10121.956] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10121.956] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10122.020] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10122.020] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10122.020] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10122.020] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10122.020] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10122.084] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10122.084] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10122.084] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10122.084] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10122.084] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10142.506] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10142.506] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10142.507] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10142.507] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10142.507] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10144.758] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10144.758] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10144.758] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10144.758] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10144.758] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10146.083] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10146.083] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10146.083] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10146.083] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10146.083] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10146.144] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10146.144] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10146.144] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10146.144] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10146.144] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10146.213] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10146.213] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10146.213] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10146.213] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10146.213] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10146.276] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10146.276] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10146.276] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10146.276] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10146.276] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10147.701] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10147.701] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10147.701] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10147.701] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10147.701] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10147.764] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10147.764] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10147.764] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10147.764] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10147.764] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10147.832] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10147.832] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10147.832] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10147.832] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10147.832] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10147.900] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10147.900] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10147.900] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10147.900] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10147.900] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10147.964] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10147.964] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10147.964] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10147.964] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10147.964] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10148.032] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10148.032] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10148.032] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10148.032] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10148.032] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10148.097] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10148.097] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10148.097] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10148.097] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10148.097] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10148.160] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10148.160] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10148.160] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10148.160] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10148.160] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10156.780] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10156.780] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10156.780] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10156.780] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10156.780] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10156.849] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10156.849] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10156.849] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10156.849] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10156.849] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10156.916] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10156.916] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10156.916] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10156.916] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10156.916] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10156.988] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10156.988] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10156.988] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10156.988] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10156.988] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.632] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.632] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.632] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.632] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.632] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.696] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.696] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.696] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.696] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.696] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.761] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.761] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.761] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.761] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.761] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.824] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.824] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.824] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.824] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.824] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.889] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.889] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.889] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.889] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.889] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10157.952] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10157.952] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10157.952] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10157.952] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10157.952] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10158.017] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10158.017] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10158.017] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10158.017] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10158.017] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10158.080] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10158.080] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10158.080] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10158.080] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10158.080] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10333.811] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10333.811] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10333.811] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10333.811] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10333.811] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10333.872] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10333.872] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10333.872] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10333.872] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10333.872] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10333.937] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10333.937] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10333.937] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10333.937] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10333.937] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10334.001] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10334.001] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10334.001] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10334.001] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10334.001] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10334.064] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10334.064] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10334.064] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10334.064] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10334.064] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10334.128] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10334.128] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10334.128] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10334.128] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10334.129] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10334.192] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10334.192] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10334.192] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10334.192] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10334.192] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10334.256] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10334.256] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10334.256] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10334.256] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10334.256] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10344.894] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10344.894] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10344.894] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10344.894] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10344.894] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10344.956] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10344.956] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10344.956] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10344.956] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10344.956] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10345.021] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10345.021] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10345.021] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10345.021] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10345.021] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10345.084] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10345.084] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10345.084] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10345.084] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10345.084] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.042] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.042] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.042] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.042] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.042] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.104] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.104] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.104] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.104] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.104] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.168] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.168] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.168] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.168] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.168] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.237] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.237] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.237] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.237] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.237] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.301] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.301] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.301] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.301] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.301] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.364] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.364] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.364] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.364] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.364] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.432] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.433] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.433] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.433] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.433] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10346.504] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10346.504] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10346.504] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10346.504] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10346.504] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10385.773] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10385.773] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10385.773] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10385.773] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10385.773] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10385.836] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10385.836] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10385.837] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10385.837] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10385.837] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10385.901] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10385.901] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10385.901] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10385.901] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10385.901] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10385.964] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10385.964] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10385.964] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10385.964] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10385.964] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10386.028] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10386.028] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10386.028] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10386.028] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10386.028] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10386.092] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10386.092] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10386.092] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10386.092] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10386.092] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10386.156] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10386.156] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10386.156] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10386.156] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10386.156] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10386.220] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10386.220] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10386.220] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10386.220] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10386.220] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.073] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.073] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.073] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.073] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.073] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.137] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.137] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.137] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.137] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.137] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.201] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.201] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.201] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.201] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.201] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.264] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.264] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.264] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.264] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.264] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.328] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.328] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.328] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.328] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.328] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.392] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.392] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.392] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.392] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.392] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.456] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.456] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.456] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.456] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.456] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10418.520] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10418.520] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10418.520] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10418.520] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10418.520] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10479.563] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10479.563] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10479.563] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10479.563] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10479.563] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10479.624] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10479.624] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10479.624] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10479.624] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10479.624] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10479.689] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10479.689] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10479.689] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10479.689] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10479.689] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10479.752] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 10479.752] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10479.752] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 10479.752] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 10479.752] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 10560.367] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 10623.701] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 11808.344] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 11828.623] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 12386.635] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 12386.635] (II) RADEON(0): Printing DDC gathered Modelines:
[ 12386.635] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 12386.635] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 12386.635] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 12639.369] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 12652.293] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 12828.284] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 12831.779] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 14343.008] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 14521.105] (II) config/udev: removing device HP Bluetooth Laser Mobile Mouse
[ 14521.136] (II) evdev: HP Bluetooth Laser Mobile Mouse: Close
[ 14521.137] (II) UnloadModule: "evdev"
[ 14769.979] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/mouse1)
[ 14769.979] (II) No input driver specified, ignoring this device.
[ 14769.979] (II) This device may have been added with another device file.
[ 14769.980] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/event13)
[ 14769.980] (**) HP Bluetooth Laser Mobile Mouse: Applying InputClass "evdev pointer catchall"
[ 14769.980] (II) Using input driver 'evdev' for 'HP Bluetooth Laser Mobile Mouse'
[ 14769.980] (**) HP Bluetooth Laser Mobile Mouse: always reports core events
[ 14769.980] (**) evdev: HP Bluetooth Laser Mobile Mouse: Device: "/dev/input/event13"
[ 14769.980] (--) evdev: HP Bluetooth Laser Mobile Mouse: Vendor 0xd62 Product 0x558
[ 14769.980] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found 3 mouse buttons
[ 14769.980] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found scroll wheel(s)
[ 14769.980] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found relative axes
[ 14769.980] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found x and y relative axes
[ 14769.980] (II) evdev: HP Bluetooth Laser Mobile Mouse: Configuring as mouse
[ 14769.980] (II) evdev: HP Bluetooth Laser Mobile Mouse: Adding scrollwheel support
[ 14769.980] (**) evdev: HP Bluetooth Laser Mobile Mouse: YAxisMapping: buttons 4 and 5
[ 14769.981] (**) evdev: HP Bluetooth Laser Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 14769.981] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/bluetooth/hci0/hci0:12/input14/event13"
[ 14769.981] (II) XINPUT: Adding extended input device "HP Bluetooth Laser Mobile Mouse" (type: MOUSE, id 14)
[ 14769.981] (II) evdev: HP Bluetooth Laser Mobile Mouse: initialized for relative axes.
[ 14769.981] (**) HP Bluetooth Laser Mobile Mouse: (accel) keeping acceleration scheme 1
[ 14769.981] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration profile 0
[ 14769.981] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration factor: 2.000
[ 14769.981] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration threshold: 4
[ 14828.601] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 15320.301] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 15320.301] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15320.301] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 15320.301] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 15320.301] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 15713.232] (II) RADEON(0): EDID vendor "LGD", prod id 708
[ 15713.232] (II) RADEON(0): Printing DDC gathered Modelines:
[ 15713.232] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz eP)
[ 15713.232] (II) RADEON(0): Modeline "1920x1080"x0.0  392.17  1920 1968 2000 2080  1080 1083 1088 1964 -hsync -vsync (188.5 kHz e)
[ 15713.232] (II) RADEON(0): Modeline "1920x1080"x0.0  396.35  1920 1940 1960 2080  1080 1083 1088 1588 -hsync -vsync (190.6 kHz e)
[ 18894.101] (II) config/udev: removing device HP Bluetooth Laser Mobile Mouse
[ 18894.133] (II) evdev: HP Bluetooth Laser Mobile Mouse: Close
[ 18894.133] (II) UnloadModule: "evdev"
[ 19083.518] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/mouse1)
[ 19083.518] (II) No input driver specified, ignoring this device.
[ 19083.518] (II) This device may have been added with another device file.
[ 19083.518] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/event13)
[ 19083.518] (**) HP Bluetooth Laser Mobile Mouse: Applying InputClass "evdev pointer catchall"
[ 19083.518] (II) Using input driver 'evdev' for 'HP Bluetooth Laser Mobile Mouse'
[ 19083.518] (**) HP Bluetooth Laser Mobile Mouse: always reports core events
[ 19083.518] (**) evdev: HP Bluetooth Laser Mobile Mouse: Device: "/dev/input/event13"
[ 19083.518] (--) evdev: HP Bluetooth Laser Mobile Mouse: Vendor 0xd62 Product 0x558
[ 19083.519] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found 3 mouse buttons
[ 19083.519] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found scroll wheel(s)
[ 19083.519] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found relative axes
[ 19083.519] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found x and y relative axes
[ 19083.519] (II) evdev: HP Bluetooth Laser Mobile Mouse: Configuring as mouse
[ 19083.519] (II) evdev: HP Bluetooth Laser Mobile Mouse: Adding scrollwheel support
[ 19083.519] (**) evdev: HP Bluetooth Laser Mobile Mouse: YAxisMapping: buttons 4 and 5
[ 19083.519] (**) evdev: HP Bluetooth Laser Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 19083.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/bluetooth/hci0/hci0:11/input15/event13"
[ 19083.519] (II) XINPUT: Adding extended input device "HP Bluetooth Laser Mobile Mouse" (type: MOUSE, id 14)
[ 19083.519] (II) evdev: HP Bluetooth Laser Mobile Mouse: initialized for relative axes.
[ 19083.519] (**) HP Bluetooth Laser Mobile Mouse: (accel) keeping acceleration scheme 1
[ 19083.519] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration profile 0
[ 19083.519] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration factor: 2.000
[ 19083.519] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration threshold: 4
[ 19984.741] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 19991.902] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 19994.013] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 19997.993] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20060.113] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20062.092] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20124.879] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20224.462] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20429.522] (II) config/udev: removing device LITE-ON Technology USB NetVista Full Width Keyboard.
[ 20429.552] (II) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Close
[ 20429.552] (II) UnloadModule: "evdev"
[ 20441.379] (II) config/udev: Adding input device LITE-ON Technology USB NetVista Full Width Keyboard. (/dev/input/event4)
[ 20441.379] (**) LITE-ON Technology USB NetVista Full Width Keyboard.: Applying InputClass "evdev keyboard catchall"
[ 20441.379] (II) Using input driver 'evdev' for 'LITE-ON Technology USB NetVista Full Width Keyboard.'
[ 20441.379] (**) LITE-ON Technology USB NetVista Full Width Keyboard.: always reports core events
[ 20441.379] (**) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Device: "/dev/input/event4"
[ 20441.379] (--) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Vendor 0x4b3 Product 0x3025
[ 20441.379] (--) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Found keys
[ 20441.379] (II) evdev: LITE-ON Technology USB NetVista Full Width Keyboard.: Configuring as keyboard
[ 20441.379] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/usb3/3-1/3-1:1.0/input/input16/event4"
[ 20441.379] (II) XINPUT: Adding extended input device "LITE-ON Technology USB NetVista Full Width Keyboard." (type: KEYBOARD, id 9)
[ 20441.379] (**) Option "xkb_rules" "evdev"
[ 20441.379] (**) Option "xkb_model" "pc105"
[ 20441.379] (**) Option "xkb_layout" "us"
[ 20441.394] (II) XKB: reuse xkmfile /var/lib/xkb/server-979EE7C0CB4F7DD92E0D4C48F3277E929EB46CDC.xkm
[ 20441.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 20479.415] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 21058.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 21082.909] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 21699.803] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 21797.060] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 21962.531] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22000.940] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22381.307] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22405.503] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22943.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22981.546] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 22997.348] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 23145.125] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 25861.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 25864.914] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 25954.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 25966.065] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 26612.468] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 26819.483] (II) XKB: reuse xkmfile /var/lib/xkb/server-95201583A4EED74B497E532150E94E19AC3117F8.xkm
[ 27974.697] (II) config/udev: removing device HP Bluetooth Laser Mobile Mouse
[ 27974.729] (II) evdev: HP Bluetooth Laser Mobile Mouse: Close
[ 27974.729] (II) UnloadModule: "evdev"
[ 29793.190] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/event13)
[ 29793.190] (**) HP Bluetooth Laser Mobile Mouse: Applying InputClass "evdev pointer catchall"
[ 29793.190] (II) Using input driver 'evdev' for 'HP Bluetooth Laser Mobile Mouse'
[ 29793.190] (**) HP Bluetooth Laser Mobile Mouse: always reports core events
[ 29793.190] (**) evdev: HP Bluetooth Laser Mobile Mouse: Device: "/dev/input/event13"
[ 29793.191] (--) evdev: HP Bluetooth Laser Mobile Mouse: Vendor 0xd62 Product 0x558
[ 29793.191] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found 3 mouse buttons
[ 29793.191] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found scroll wheel(s)
[ 29793.191] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found relative axes
[ 29793.191] (--) evdev: HP Bluetooth Laser Mobile Mouse: Found x and y relative axes
[ 29793.191] (II) evdev: HP Bluetooth Laser Mobile Mouse: Configuring as mouse
[ 29793.191] (II) evdev: HP Bluetooth Laser Mobile Mouse: Adding scrollwheel support
[ 29793.191] (**) evdev: HP Bluetooth Laser Mobile Mouse: YAxisMapping: buttons 4 and 5
[ 29793.191] (**) evdev: HP Bluetooth Laser Mobile Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 29793.191] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/bluetooth/hci0/hci0:12/input17/event13"
[ 29793.191] (II) XINPUT: Adding extended input device "HP Bluetooth Laser Mobile Mouse" (type: MOUSE, id 14)
[ 29793.191] (II) evdev: HP Bluetooth Laser Mobile Mouse: initialized for relative axes.
[ 29793.191] (**) HP Bluetooth Laser Mobile Mouse: (accel) keeping acceleration scheme 1
[ 29793.192] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration profile 0
[ 29793.192] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration factor: 2.000
[ 29793.192] (**) HP Bluetooth Laser Mobile Mouse: (accel) acceleration threshold: 4
[ 29793.192] (II) config/udev: Adding input device HP Bluetooth Laser Mobile Mouse (/dev/input/mouse1)
[ 29793.192] (II) No input driver specified, ignoring this device.
[ 29793.192] (II) This device may have been added with another device file.
```

---

### Post by Yellow Pasque on 2014-03-31
> **parashep said:**
> I noticed it does say using 8 bits per channel as the driver initializes, but when it's detecting the monitor it says: "[    25.325] (II) RADEON(0): 6 bits per channel". I wonder why?

I think you are confused. 6-bit probably means you have a monitor with dithering: [http://compreviews.about.com/od/multimedia/a/LCDColor.htm](http://compreviews.about.com/od/multimedia/a/LCDColor.htm)

This is the important part, and it is correct:
```
[    25.231] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    25.231] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    25.231] (==) RADEON(0): Default visual is TrueColor
[    25.231] (==) RADEON(0): RGB weight 888
```

The rest of the log looks okay, so I don't know how to further troubleshoot. Are you using any sort of adapter (like DVI -> HDMI)? Is there any setting on your disply for color temperature or such?

---

### Post by parashep on 2014-03-31
actually, this is a laptop, and this is the built-in display. it may be a display that employs dithering (which would kinda suck since I didn't get a good look at it beforehand), but in that case it's definitely not doing its job.
something that I just remembered is that it's a 3D display, if that makes a difference. I don't use 3D ever.

here's a shot of a default wallpaper. pretty extreme, but anything with such close colour values will band.
[IMG]https://dl.dropboxusercontent.com/u/88868/Images/badbanding.jpg[/IMG]

EDIT: yeah, unfortunately it's most definitely a monitor that dithers down a 8bit per channel signal to a 6bit per channel signal. there's a big difference there, but, to do the dithering in the first place, the monitor would have to be passed the full 24-bit depth signal in the first place, which I don't think is happening... can I configure it so that it *does* happen?

I don't know if the display does the dithering via hardware if it is passed a 24bit signal, or if the software does it first then passes an 18bit signal to the display...

---

