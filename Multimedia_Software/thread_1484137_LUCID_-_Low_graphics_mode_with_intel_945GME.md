---
title: "LUCID - Low graphics mode with intel 945GME"
date: 2010-05-15
forum: Multimedia Software
---

### Post by Praetor77 on 2010-05-15
Greetings, after upgrading my UNR 9.10 to 10.04 everything seemed to work perfect upon my first restart, but after my second...
"Running in low graphics mode: Your hardware cannot be detected".

I have an Asus 1005HA (graphics card INTEL 945GME).

Here is my lspci -vvv:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8340
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at dc00 [size=8]
    Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at f7dc0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915
```
My xorg.cong.failsafe was using VESA, but changing it to intel worked, and I have much better performance.
Anyways, after trying to disable KMS using "i915.modeset=0", I recieved:
```
(EE) intel(0): No modes.
(EE) Screen(s) found, but none have usable configuration.
``` I found forcing KMS by using "i915.modeset=1", I no longer recieved the errors posted here, but I still get low graphics mode.

I tried everything listed here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

So now I am using mainstream rc7 kernel and 2.11 xserver-xorg-intel driver. I edited my xorg.conf file to using EXA rendering, but still running in low graphics mode.

The error when I get the low graphics mode message says my hardware could not be detected, but judging from my xorg logfiles ( xorg.conf put together by myself using the wiki and also from dpkg-reconfigure xserver-xorg) everything should be working okay?!

When trying to let LUCID auto-detect my xorg config (xorg.conf.d directory), I get this xorg log:


```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux rodrigo-laptop 2.6.34-020634rc7-generic #020634rc7 SMP Mon May 10 10:08:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634rc7-generic root=UUID=75a7c909-751f-4712-bb7a-32096e7997bc ro crashkernel=384M-2G:64M,2G-:128M i915.modeset=1 quiet splash acpi_osi=Linux
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 15 00:55:19 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27ae:1043:8340 Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7dc0000/262144, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:27a6:1043:8340 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf7e80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.11.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(==) intel(0): video overlay key set to 0x101fe

```When using this xorg.conf file (Tried commenting all the options and VideoRam with no avail):

```
Section "Device"
        Identifier           "Configured Video Device"
        Driver "intel"
    Option     "FramebufferCompression" "on"
    Option     "AccelMethod" "EXA"
    Option     "Tiling" "on"
    Option "MigrationHeuristic" "greedy"
    Option "XvMC" "true"
    VideoRam 261376
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    # Uncomment if your screen resolution is 1024x600
    DisplaySize 195 113
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Virtual    1024 600
    EndSubSection    
EndSection
```I get this xorg.5.log (I have logs from 0 through 5) (11:48:01am):

```
X.Org X Server 1.7.6

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux rodrigo-laptop 2.6.34-020634rc7-generic #020634rc7 SMP Mon May 10 10:08:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634rc7-generic root=UUID=75a7c909-751f-4712-bb7a-32096e7997bc ro crashkernel=384M-2G:64M,2G-:128M i915.modeset=1 quiet splash acpi_osi=Linux
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Sat May 15 11:48:01 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27ae:1043:8340 Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7dc0000/262144, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:27a6:1043:8340 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf7e80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.11.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "Tiling" "on"
(**) intel(0): Option "XvMC" "true"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(==) intel(0): video overlay key set to 0x101fe

```And this posterior xorg.failsafe.log (11:48:02am)
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux rodrigo-laptop 2.6.34-020634rc7-generic #020634rc7 SMP Mon May 10 10:08:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634rc7-generic root=UUID=75a7c909-751f-4712-bb7a-32096e7997bc ro crashkernel=384M-2G:64M,2G-:128M i915.modeset=1 quiet splash acpi_osi=Linux
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Sat May 15 11:48:02 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:27ae:1043:8340 Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7dc0000/262144, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:27a6:1043:8340 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf7e80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) FBDEV: driver for framebuffer: fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(**) FBDEV(0): claimed PCI slot 0@0:2:0
(II) FBDEV(0): using default device
(II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: inteldrmfb (video memory: 2400kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x600 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current"
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(==) FBDEV(0): Backing store disabled
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(==) FBDEV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-EEE76AC18E53EDE3D19E026307AE3E38C6676B05.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event5)
(**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
(**) USB 2.0 Camera: always reports core events
(**) USB 2.0 Camera: Device: "/dev/input/event5"
(II) USB 2.0 Camera: Found keys
(II) USB 2.0 Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Asus EeePC extra buttons (/dev/input/event7)
(**) Asus EeePC extra buttons: Applying InputClass "evdev keyboard catchall"
(**) Asus EeePC extra buttons: always reports core events
(**) Asus EeePC extra buttons: Device: "/dev/input/event7"
(II) Asus EeePC extra buttons: Found keys
(II) Asus EeePC extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```
Only error I find in my logs is in my boot.log:


```
fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 349614/1044480 files, 3024287/4170867 blocks (check in 2 mounts)
init: ureadahead-other main process (808) terminated with status 4  
 * Setting sensors limits       [128G  [122G[ OK ]
 * Loading cpufreq kernel modules...       [128G  [122G[ OK ]
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...       [128G  * CPU0...       [128G  * CPU1...       [128G  [122G[ OK ] 
```Going crazy here, looking for help. I really have doubts that anything is going wrong, other than monitors not being detected (aside from my default monitor trouble, when I plug in a VGA monitor and try to detect it I get nothing...).
Thanks in advance to anyone who can help me!

---

### Post by Praetor77 on 2010-05-15
I was reading over my post, and wondering what all these fbdev errors were if I´m supposed to be using the i915 driver, and when sudo gedit /etc/X11/xorg.conf.failsafe I find:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Why?:confused:

---

### Post by nmsmith on 2010-05-15
Agreed: our problems look similar. Especially the sense in which it might be an incorrect monitor detection. Still, the different hardware suggests to me that there will by equally different solutions.

---

### Post by Praetor77 on 2010-05-18
Finally resolved this problem by downloading and installing latest libdrm from here:
[http://dri.freedesktop.org/libdrm/libdrm-2.4.20.tar.bz2](http://dri.freedesktop.org/libdrm/libdrm-2.4.20.tar.bz2)

---

### Post by valhemmer on 2010-05-18
hey i have this same problem and im basicaly a noob. how do i go about install that libdrm?

---

### Post by mklinux on 2010-06-17
Bump - I have an intel 945gme graphics driver too, and my computer keeps on booting into the command mode in which it won't connect to the internet and can't sudo apt-get update and furthermore won't reset the graphics drivers correctly. Is there any way to solve this problem...?

---

### Post by intheflesh on 2010-06-17
> **valhemmer said:**
> hey i have this same problem and im basicaly a noob. how do i go about install that libdrm?

You need to download it and uncompress it. The command is:
```
$ bzip2 -u libdrm-2.4.20.tar.bz2
```
Then you have to untar it:
```
$ tar xf libdrm-2.4.20.tar
```
After that, navigate to the directory in which the archive was uncompressed:
```
$ cd libdrm-2.4.20/
```
And refer to README for instructions:
```
$ cat README
```

Basically, it's a CMMI set commands. You will have to prepend each one with sudo.

Of course, you do not enter dollar sign before anything, tht's just prompt. :)

---

### Post by mklinux on 2010-06-19
The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) intel(0): Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.

I've tried all of the workarounds previously mentioned above and I cannot connect to the internet to download any of the mentioned files.

Any ideas? I'm desperate and I'd rather not reinstall again...I've had to reinstall Ubuntu more than my previous operating system (windows) now... :(

---

### Post by bach on 2010-07-01
I am having the same problem with Ubuntu 10.04 64 bits on a DELL 6510 notebook with integrated Intel graphics. I can only boot using the kernel option "i915.modeset=0". The machine only boots in low-graphics mode. In the logs, I see

(EE) intel(0): No kernel modesetting driver detected
(EE) Screen(s) found, but none have a usable configuration

Any suggestions? Thanks.

---

### Post by rlzaleski on 2010-07-02
I was getting the black screen when my comp booted to X.  Normally Ubuntu is so good about video configuration I didn't even think drivers, but I guess the chipset in this 2 week old Dell desktop is too new, Oh well, that's the way of linux.

Anyways, it's running good, to get it there I did the following.

```

sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

```

I would also recommend you remove your **xorg.conf** as that's how I'm running, ubuntu/xorg will auto configure everything on startup.

```

sudo rm /etc/X11/xorg.conf

```

Then reboot and hope for the best.  Assuming that works, then double check things after you log in via

```

sudo apt-get install mesa-utils
glxinfo 

```

You should get a whole bunch of text, the important lines are towards the top

```

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G45/G43 GEM 20091221 2009Q4 x86/MMX/SSE2
...

```

Note there's there's a server, client, and OpenGL vendor string, you want the **OpenGL** one.  The Intel line may change a bit too.  If that all works the last thing to do is

```

glxgears

```Which if you let it run for awhile and don't move the mouse, it'll calculate the FPS, I run it in it's default windowed size and maximized and I'm getting 4,800 and 300 FPS, which isn't bad.

Hopefully this won't freak out again.  Hope that helps someone.

---

### Post by bach on 2010-07-07
rlzaleski: The problem remains here (notebook DELL 6510 with Intel integrated graphics card). I have 

cribari@darwin:~$ dpkg -l | grep xserver | grep intel
ii  xserver-xorg-video-intel                  2:2.12.0+git20100705~glasen~ppa1                X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-intel-dbg              2:2.12.0+git20100705~glasen~ppa1                X.Org X server -- Intel i8xx, i9xx display driver (debug symbols

cribari@darwin:~$ dpkg -l | grep mesa-utils
ii  mesa-utils                                7.7.1-1ubuntu3                                  Miscellaneous Mesa GL utilities

cribari@darwin:~$ glxinfo | grep rendering
direct rendering: Yes
cribari@darwin:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

I still get a blank screen when I boot the computer, unless I use the kernel option "i915.modeset=0".

Suggestions are welcome.

---

### Post by orsty9001 on 2010-08-29
I've got this problem too. 

```
(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
DRM_IOCTL_I915_GEM_APERTURE failed: Bad file descriptor
Assuming 131072kB available aperture size.
May lead to reduced performance or incorrect rendering.
get chip id failed: -1 [9]
param: 4, val: 0
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

glxinfo just says that it's unable to open display.

---

### Post by Kognit on 2010-09-13
Hi guys

I have intel gma 4500M and i have this strange problem.Compiz and the graphic is really cool in gnome but if i "log in" in Openbox window manager (or when i use gnome without special effects), the windows behave strange - when i move them, the edges of windows are somewhat sticky and they are not smooth. I have a blank xorg.conf, though.

Any suggestions?
thx

---

### Post by shinwadone on 2010-11-23
it did work!!
as soon as the driver update, the display changed immediately!


> **rlzaleski said:**
> I was getting the black screen when my comp booted to X.  Normally Ubuntu is so good about video configuration I didn't even think drivers, but I guess the chipset in this 2 week old Dell desktop is too new, Oh well, that's the way of linux.

Anyways, it's running good, to get it there I did the following.

```

sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

```

I would also recommend you remove your **xorg.conf** as that's how I'm running, ubuntu/xorg will auto configure everything on startup.

```

sudo rm /etc/X11/xorg.conf

```

Then reboot and hope for the best.  Assuming that works, then double check things after you log in via

```

sudo apt-get install mesa-utils
glxinfo 

```

You should get a whole bunch of text, the important lines are towards the top

```

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G45/G43 GEM 20091221 2009Q4 x86/MMX/SSE2
...

```

Note there's there's a server, client, and OpenGL vendor string, you want the **OpenGL** one.  The Intel line may change a bit too.  If that all works the last thing to do is

```

glxgears

```Which if you let it run for awhile and don't move the mouse, it'll calculate the FPS, I run it in it's default windowed size and maximized and I'm getting 4,800 and 300 FPS, which isn't bad.

Hopefully this won't freak out again.  Hope that helps someone.

---

### Post by Pnin on 2010-12-10
This didn't really solve my lowres woes, but it helped some. Thanks anyway. :D

Here's my report, as posted at launchpad.net:
[URL="https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532579"]```
https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532579
```[/URL]> Problem: Having installed Linux Mint 9 LXDE on an elderly HP Vectra VL400 workstation (PIII 1GHz, 512MB RAM, 20GB HDD), the graphic UI was available, but my maximum resolution would be 800x600x60Hz and I had no 'xorg.conf' file in '/etc/X11/'. Querying with lspci returned the following adapter identification:

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)

Thus began my two day ordeal. After searching high and low, reading leaft and right, a lot of brow wrinkling, pencil sucking, and hair pulling, I was exactly where I started, with zero results. I saw [... **here**] how this predicament could be solved by installing the latest libdrm, which I did to no avail. I even tried building a new xorg.conf by hand (as per [http://forums.linuxmint.com/viewtopic.php?f=175&t=58781#p336104](http://forums.linuxmint.com/viewtopic.php?f=175&t=58781#p336104)), and failed miserably, attesting to the real depth of my noobiness. The system wouldn't even start, so I had to launch the livecd to delete that xorg.conf...

But eventually that was the seed for the solution: after some more editing, including the Section "Module" suggested by TJ, I rebooted and everything automagically worked -- without further ado, I now have 1024x768x85Hz, which is rather more bearable to work with.

Here's the healing xorg.conf:

```
----- xorg.conf -----

Section "Device"
	Identifier	"Intel Corporation 82815 CGC"
	Driver		"intel"
#	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"DEC"
	ModelName	"VRT17-HA"
	Option		"DPMS"
	HorizSync	29-82
	VertRefresh	50-150
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC"
	Monitor		"Monitor0"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Server Layout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Module"
	Load		"vesa"
EndSection
```

May it help others stuck with such a hairy problem. Now, I must solve the remaining ones... ;)

---

### Post by stoogiebuncho on 2010-12-19
> **rlzaleski said:**
> I was getting the black screen when my ***p booted to X.  Normally Ubuntu is so good about video configuration I didn't even think drivers, but I guess the chipset in this 2 week old Dell desktop is too new, Oh well, that's the way of linux.

Anyways, it's running good, to get it there I did the following.

```

sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

```

I would also re***mend you remove your **xorg.conf** as that's how I'm running, ubuntu/xorg will auto configure everything on startup.

```

sudo rm /etc/X11/xorg.conf

```

Then reboot and hope for the best.  Assuming that works, then double check things after you log in via

```

sudo apt-get install mesa-utils
glxinfo 

```

You should get a whole bunch of text, the important lines are towards the top

```

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G45/G43 GEM 20091221 2009Q4 x86/MMX/SSE2
...

```

Note there's there's a server, client, and OpenGL vendor string, you want the **OpenGL** one.  The Intel line may change a bit too.  If that all works the last thing to do is

```

glxgears

```Which if you let it run for awhile and don't move the mouse, it'll calculate the FPS, I run it in it's default windowed size and maximized and I'm getting 4,800 and 300 FPS, which isn't bad.

Hopefully this won't freak out again.  Hope that helps someone.

I followed these instructions and I think it made think it might have made things worse for me.  How do I roll back to the default driver?

---

### Post by h8train on 2013-03-06
> **rlzaleski said:**
> I was getting the black screen when my comp booted to X.  Normally Ubuntu is so good about video configuration I didn't even think drivers, but I guess the chipset in this 2 week old Dell desktop is too new, Oh well, that's the way of linux.

Anyways, it's running good, to get it there I did the following.

```

sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

```

I would also recommend you remove your **xorg.conf** as that's how I'm running, ubuntu/xorg will auto configure everything on startup.

```

sudo rm /etc/X11/xorg.conf

```

Then reboot and hope for the best.  Assuming that works, then double check things after you log in via

```

sudo apt-get install mesa-utils
glxinfo 

```

You should get a whole bunch of text, the important lines are towards the top

```

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G45/G43 GEM 20091221 2009Q4 x86/MMX/SSE2
...

```

Note there's there's a server, client, and OpenGL vendor string, you want the **OpenGL** one.  The Intel line may change a bit too.  If that all works the last thing to do is

```

glxgears

```Which if you let it run for awhile and don't move the mouse, it'll calculate the FPS, I run it in it's default windowed size and maximized and I'm getting 4,800 and 300 FPS, which isn't bad.

Hopefully this won't freak out again.  Hope that helps someone.


This helped me after pulling hair for a couple hours.

Thank you.

Rich

---

### Post by wildmanne39 on 2013-03-07
Old thread closed!

---

