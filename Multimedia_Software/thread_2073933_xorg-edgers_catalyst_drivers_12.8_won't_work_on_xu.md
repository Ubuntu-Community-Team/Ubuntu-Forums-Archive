---
title: "xorg-edgers catalyst drivers 12.8 won't work on xubuntu 12.04"
date: 2012-10-20
forum: Multimedia Software
---

### Post by supernater on 2012-10-20
I just installed xubuntu and I wanted to update to the latest catalyst driver.  I added the xorg-edgers ppa and updated.  The update added a lot of packages which included...

Install:
linux-image-3.5.0-17-generic:amd64
libdrm-nouveau2:amd64
linux-headers-3.5.0-17-generic:amd64
libtxc-dxtn-s2tc0:amd64
linux-headers-3.5.0-17:amd64
linux-image-extra-3.5.0-17-generic:amd64
libllvm3.1:amd64

Upgrade:
fglrx-amdcccle:amd64
fglrx:amd64
libcairo-gobject2:amd64
libcairo2:amd64
libdrm-intel1:amd64
libdrm-nouveau1a:amd64
libdrm-radeon1:amd64
libdrm2:amd64
libgl1-mesa-dri:amd64
libgl1-mesa-glx:amd64
libglapi-mesa:amd64
libglu1-mesa:amd64
libmtdev1:amd64
libpciaccess0:amd64
libpixman-1-0:amd64
libxatracker1:amd64
linux-firmware:amd64
linux-generic:amd64
linux-headers-generic:amd64
linux-image-generic:amd64
linux-libc-dev:amd64
xserver-common:amd64
xserver-xorg-core:amd64
xserver-xorg-input-evdev:amd64
xserver-xorg-input-mouse:amd64
xserver-xorg-input-synaptics:amd64
xserver-xorg-input-vmmouse:amd64
xserver-xorg-input-wacom:amd64
xserver-xorg-video-ati:amd64
xserver-xorg-video-cirrus:amd64
xserver-xorg-video-fbdev:amd64
xserver-xorg-video-intel:amd64
xserver-xorg-video-mach64:amd64
xserver-xorg-video-mga:amd64
xserver-xorg-video-neomagic:amd64
xserver-xorg-video-nouveau:amd64
xserver-xorg-video-openchrome:amd64
xserver-xorg-video-qxl:amd64
xserver-xorg-video-r128:amd64
xserver-xorg-video-radeon:amd64
xserver-xorg-video-s3:amd64
xserver-xorg-video-savage:amd64
xserver-xorg-video-siliconmotion:amd64
xserver-xorg-video-sis:amd64
xserver-xorg-video-sisusb:amd64
xserver-xorg-video-tdfx:amd64
xserver-xorg-video-trident:amd64
xserver-xorg-video-vesa:amd64
xserver-xorg-video-vmware:amd64

When I restarted I could not get xserver to start.  The xorg log showed...

```
[    19.282] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    19.282] X Protocol Version 11, Revision 0
[    19.282] Build Operating System: Linux 2.6.24-29-xen x86_64 Ubuntu
[    19.282] Current Operating System: Linux lin-pc 3.5.0-17-generic #26-Ubuntu SMP Thu Oct 4 16:00:30 UTC 2012 x86_64
[    19.282] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=76d5a52f-7eeb-4e35-a4de-8882cb90f546 ro quiet splash vt.handoff=7
[    19.282] Build Date: 09 July 2012  05:20:18PM
[    19.282] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support) 
[    19.282] Current version of pixman: 0.26.0
[    19.282] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.282] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.282] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 20 13:51:09 2012
[    19.282] (==) Using config file: "/etc/X11/xorg.conf"
[    19.283] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.283] (==) No Layout section.  Using the first Screen section.
[    19.283] (**) |-->Screen "Default Screen" (0)
[    19.283] (**) |   |-->Monitor "<default monitor>"
[    19.283] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    19.283] (==) Automatically adding devices
[    19.283] (==) Automatically enabling devices
[    19.283] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.283] 	Entry deleted from font path.
[    19.283] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    19.283] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.283] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.283] (II) Loader magic: 0x7f32d3424b00
[    19.283] (II) Module ABI versions:
[    19.283] 	X.Org ANSI C Emulation: 0.4
[    19.283] 	X.Org Video Driver: 12.0
[    19.283] 	X.Org XInput driver : 16.0
[    19.283] 	X.Org Server Extension : 6.0
[    19.283] (--) PCI:*(0:1:0:0) 1002:6898:1458:21e5 rev 0, Mem @ 0xe0000000/268435456, 0xf7e20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    19.283] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.283] (II) "extmod" will be loaded by default.
[    19.283] (II) "dbe" will be loaded by default.
[    19.283] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    19.283] (II) "record" will be loaded by default.
[    19.283] (II) "dri" will be loaded by default.
[    19.283] (II) "dri2" will be loaded by default.
[    19.283] (II) LoadModule: "glx"
[    19.283] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    19.284] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    19.284] 	compiled for 6.9.0, module version = 1.0.0
[    19.284] (II) Loading extension GLX
[    19.284] (II) LoadModule: "extmod"
[    19.284] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.284] (II) Module extmod: vendor="X.Org Foundation"
[    19.284] 	compiled for 1.12.3, module version = 1.0.0
[    19.284] 	Module class: X.Org Server Extension
[    19.284] 	ABI class: X.Org Server Extension, version 6.0
[    19.284] (II) Loading extension MIT-SCREEN-SAVER
[    19.284] (II) Loading extension XFree86-VidModeExtension
[    19.284] (II) Loading extension XFree86-DGA
[    19.284] (II) Loading extension DPMS
[    19.284] (II) Loading extension XVideo
[    19.284] (II) Loading extension XVideo-MotionCompensation
[    19.284] (II) Loading extension X-Resource
[    19.284] (II) LoadModule: "dbe"
[    19.284] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.284] (II) Module dbe: vendor="X.Org Foundation"
[    19.284] 	compiled for 1.12.3, module version = 1.0.0
[    19.284] 	Module class: X.Org Server Extension
[    19.284] 	ABI class: X.Org Server Extension, version 6.0
[    19.284] (II) Loading extension DOUBLE-BUFFER
[    19.284] (II) LoadModule: "record"
[    19.284] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.284] (II) Module record: vendor="X.Org Foundation"
[    19.284] 	compiled for 1.12.3, module version = 1.13.0
[    19.284] 	Module class: X.Org Server Extension
[    19.284] 	ABI class: X.Org Server Extension, version 6.0
[    19.284] (II) Loading extension RECORD
[    19.284] (II) LoadModule: "dri"
[    19.284] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.284] (II) Module dri: vendor="X.Org Foundation"
[    19.284] 	compiled for 1.12.3, module version = 1.0.0
[    19.284] 	ABI class: X.Org Server Extension, version 6.0
[    19.284] (II) Loading extension XFree86-DRI
[    19.284] (II) LoadModule: "dri2"
[    19.285] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.285] (II) Module dri2: vendor="X.Org Foundation"
[    19.285] 	compiled for 1.12.3, module version = 1.2.0
[    19.285] 	ABI class: X.Org Server Extension, version 6.0
[    19.285] (II) Loading extension DRI2
[    19.285] (==) Matched fglrx as autoconfigured driver 0
[    19.285] (==) Matched ati as autoconfigured driver 1
[    19.285] (==) Matched vesa as autoconfigured driver 2
[    19.285] (==) Matched fbdev as autoconfigured driver 3
[    19.285] (==) Assigned the driver to the xf86ConfigLayout
[    19.285] (II) LoadModule: "fglrx"
[    19.285] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    19.292] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    19.292] 	compiled for 1.4.99.906, module version = 8.98.2
[    19.292] 	Module class: X.Org Video Driver
[    19.292] (II) Loading sub module "fglrxdrm"
[    19.292] (II) LoadModule: "fglrxdrm"
[    19.292] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.292] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    19.292] 	compiled for 1.4.99.906, module version = 8.98.2
[    19.292] (II) LoadModule: "ati"
[    19.293] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    19.293] (II) Module ati: vendor="X.Org Foundation"
[    19.293] 	compiled for 1.12.3, module version = 6.99.99
[    19.293] 	Module class: X.Org Video Driver
[    19.293] 	ABI class: X.Org Video Driver, version 12.0
[    19.293] (II) LoadModule: "radeon"
[    19.293] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    19.293] (II) Module radeon: vendor="X.Org Foundation"
[    19.293] 	compiled for 1.12.3, module version = 6.99.99
[    19.293] 	Module class: X.Org Video Driver
[    19.293] 	ABI class: X.Org Video Driver, version 12.0
[    19.293] (II) LoadModule: "vesa"
[    19.293] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.293] (II) Module vesa: vendor="X.Org Foundation"
[    19.293] 	compiled for 1.12.3, module version = 2.3.2
[    19.293] 	Module class: X.Org Video Driver
[    19.293] 	ABI class: X.Org Video Driver, version 12.0
[    19.293] (II) LoadModule: "fbdev"
[    19.293] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.293] (II) Module fbdev: vendor="X.Org Foundation"
[    19.293] 	compiled for 1.12.3, module version = 0.4.3
[    19.293] 	Module class: X.Org Video Driver
[    19.293] 	ABI class: X.Org Video Driver, version 12.0
[    19.293] (II) AMD Proprietary Linux Driver Version Identifier:8.98.2
[    19.293] (II) AMD Proprietary Linux Driver Release Identifier: 8.98                                 
[    19.293] (II) AMD Proprietary Linux Driver Build Date: Jun 11 2012 11:57:59
[    19.293] (II) RADEON: Driver for ATI Radeon chipsets:
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
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE
[    19.295] (II) VESA: driver for VESA chipsets: vesa
[    19.295] (II) FBDEV: driver for framebuffer: fbdev
[    19.295] (--) using VT number 7

[    19.303] (WW) Falling back to old probe method for fglrx
[    19.305] (II) Loading PCS database from /etc/ati/amdpcsdb
[    19.306] (--) Assigning device section with no busID to primary device
[    19.306] (--) Chipset Supported AMD Graphics Processor (0x6898) found
[    19.306] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    19.306] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.306] (II) AMD Video driver is signed
[    19.306] (II) fglrx(0): pEnt->device->identifier=0x7f32d31d723f
[    19.306] (WW) Falling back to old probe method for vesa
[    19.306] (WW) Falling back to old probe method for fbdev
[    19.306] (II) Loading sub module "fbdevhw"
[    19.306] (II) LoadModule: "fbdevhw"
[    19.307] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.307] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.307] 	compiled for 1.12.3, module version = 0.0.2
[    19.307] 	ABI class: X.Org Video Driver, version 12.0
[    19.307] (II) fglrx(0): === [xdl_xs112_atiddxPreInit] === begin
[    19.307] (II) Loading sub module "vgahw"
[    19.307] (II) LoadModule: "vgahw"
[    19.307] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.307] (II) Module vgahw: vendor="X.Org Foundation"
[    19.307] 	compiled for 1.12.3, module version = 0.1.0
[    19.307] 	ABI class: X.Org Video Driver, version 12.0
[    19.307] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    19.307] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    19.307] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.307] (==) fglrx(0): Default visual is TrueColor
[    19.307] (==) fglrx(0): RGB weight 888
[    19.307] (II) fglrx(0): Using 8 bits per RGB 
[    19.307] (==) fglrx(0): Buffer Tiling is ON
[    19.307] (II) Loading sub module "fglrxdrm"
[    19.307] (II) LoadModule: "fglrxdrm"
[    19.307] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    19.307] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    19.307] 	compiled for 1.4.99.906, module version = 8.98.2
[    19.308] ukiDynamicMajor: failed to open /proc/ati/major
[    19.308] ukiDynamicMajor: failed to open /proc/ati/major
[    19.308] (**) fglrx(0): NoAccel = NO
[    19.308] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    19.308] (--) fglrx(0): Chipset: "ATI Radeon HD 5800 Series" (Chipset = 0x6898)
[    19.308] (--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0x21e5)
[    19.308] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    19.308] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    19.308] (--) fglrx(0): MMIO registers at 0xf7e20000
[    19.308] (--) fglrx(0): I/O port at 0x0000e000
[    19.308] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    19.309] 
[    19.309] Backtrace:
[    19.309] 0: /usr/bin/X (xorg_backtrace+0x34) [0x7f32d31ba584]
[    19.309] 1: /usr/bin/X (0x7f32d3034000+0x18a36a) [0x7f32d31be36a]
[    19.309] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f32d235a000+0xfcb0) [0x7f32d2369cb0]
[    19.309] 3: /usr/lib/x86_64-linux-gnu/libpciaccess.so.0 (0x7f32d2577000+0x4dd4) [0x7f32d257bdd4]
[    19.309] 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (0x7f32ce7df000+0x803489) [0x7f32cefe2489]
[    19.309] 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (amd_xs112_int10_xf86ExtendedInitInt10+0xdd) [0x7f32cefe221d]
[    19.310] 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (amd_xs112_int10_xf86InitInt10+0xb) [0x7f32cefe1abb]
[    19.310] 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xf86InitInt10+0xd) [0x7f32ceb27b3d]
[    19.310] 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (0x7f32ce7df000+0x48421c) [0x7f32cec6321c]
[    19.310] 9: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs112_PreInitAdapter+0x274) [0x7f32cec62df4]
[    19.310] 10: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs112_atiddxPreInit+0x12ad) [0x7f32cec644dd]
[    19.310] 11: /usr/bin/X (InitOutput+0x9c8) [0x7f32d30c3268]
[    19.310] 12: /usr/bin/X (0x7f32d3034000+0x3d70d) [0x7f32d307170d]
[    19.310] 13: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f32d11eb76d]
[    19.310] 14: /usr/bin/X (0x7f32d3034000+0x3dbd1) [0x7f32d3071bd1]
[    19.310] 
[    19.310] Segmentation fault at address 0xffffffffd40b6932
[    19.310] 
Caught signal 11 (Segmentation fault). Server aborting
[    19.310] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    19.310] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    19.310] 
[    19.328]  ddxSigGiveUp: Closing log
[    19.331] Server terminated with error (1). Closing log file.
```


I removed fglrx and fglrx-amdcccle and I was able to startx.  I would like to fix this if possible without reinstalling Xubuntu.  Any suggestions?

---

### Post by Yellow Pasque on 2012-10-20
Remove Catalyst: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Note that if you try to reinstall Catalyst, you shouldn't install kernel 3.5, since Catalyst doesn't support it yet.

---

### Post by supernater on 2012-10-20
> **Temüjin said:**
> Remove Catalyst: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Note that if you try to reinstall Catalyst, you shouldn't install kernel 3.5, since Catalyst doesn't support it yet.

I don't understand.  I want to install Catalyst 12.8, not remove it.  When I do that using the xorg-edgers ppa, it does not work.

---

### Post by Yellow Pasque on 2012-10-20
When you use the xorg-edgers ppa, it installs kernel 3.5. That's not what you want. Just follow these steps: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by supernater on 2012-10-20
Oh, I see what you mean.  I will try it.  However, do I have to reinstall the driver every time I update my kernel?

---

### Post by Yellow Pasque on 2012-10-20
dkms will take care of new kernels automatically.

---

### Post by supernater on 2012-10-20
In that tutorial there is a step...

> If you are using the x86_64 architecture (64 bit):

sudo apt-get install ia32-libs-multiarch:i386 lib32gcc1 libc6-i386
sudo apt-get install ia32-libs
cd /usr ; sudo ln -svT lib /usr/lib64

In Xubuntu 64bit, I do not see a ia32-libs-multiarch in synaptic.  I am using Xubuntu 12.04 64 bit.  Should I skip this?  I cannot install ia32-libs without it.

Edit:
Found a solution here...
[https://bugs.launchpad.net/ubuntu/quantal/+source/nspr/+bug/1049840](https://bugs.launchpad.net/ubuntu/quantal/+source/nspr/+bug/1049840)

Had do downgrade libnspr4 and libnspr4-0d and then I could install ia32-libs-multiarch:i386.  Installing this installed a lot of other packages also.

---

### Post by supernater on 2012-10-21
That guide worked great.  The only trouble came when I had to install ia32-libs and ia32-libs-multiarch, there were a lot of additional packages that had to be installed.  Anyway, thank you Temujin for your help!  I wish I'd found that guide earlier.  Usually xorg-edgers never gives me any problems.  This time they really let me down :(

---

