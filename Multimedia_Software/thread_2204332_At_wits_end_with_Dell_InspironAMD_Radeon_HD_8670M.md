---
title: "At wits end with Dell Inspiron/AMD Radeon HD 8670M"
date: 2014-02-07
forum: Multimedia Software
---

### Post by felgro on 2014-02-07
Hello,

I purchased a Dell Inspiron 3537 based on it being available elsewhere as a preinstalled system -

[http://www.ubuntu.com/certification/hardware/201305-13649/](http://www.ubuntu.com/certification/hardware/201305-13649/)

And the fact that in 10 years of Dell/Linux use at home and work I've never had a problem. Until now. This unit shipped with a Radeon 8670M adapter and it is an absolute disaster area. After 3 days of trying, the best I've been able to get is a login screen - which leads to a dead black screen, occasionally with blinking cursor. None of the online information I have found has been of any use. I'm using standard Ubuntu64 13.10 and the beta driver from AMD (the "blessed" only supports 13.04) -

[http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64)

As far as I can see from running lspci -kvm, the driver has installed successfully -

```
Device:    00:00.0
Class:    Host bridge
Vendor:    Intel Corporation
Device:    Haswell-ULT DRAM Controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    09

Device:    00:02.0
Class:    VGA compatible controller
Vendor:    Intel Corporation
Device:    Haswell-ULT Integrated Graphics Controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    09
Driver:    i915

Device:    00:03.0
Class:    Audio device
Vendor:    Intel Corporation
Device:    Device 0a0c
SVendor:    Dell
SDevice:    Device 05ea
Rev:    09
Driver:    snd_hda_intel

Device:    00:14.0
Class:    USB controller
Vendor:    Intel Corporation
Device:    Lynx Point-LP USB xHCI HC
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
ProgIf:    30
Driver:    xhci_hcd

Device:    00:16.0
Class:    Communication controller
Vendor:    Intel Corporation
Device:    Lynx Point-LP HECI #0
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
Driver:    mei_me

Device:    00:1b.0
Class:    Audio device
Vendor:    Intel Corporation
Device:    Lynx Point-LP HD Audio Controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
Driver:    snd_hda_intel

Device:    00:1c.0
Class:    PCI bridge
Vendor:    Intel Corporation
Device:    Lynx Point-LP PCI Express Root Port 3
Rev:    e4
Driver:    pcieport

Device:    00:1c.3
Class:    PCI bridge
Vendor:    Intel Corporation
Device:    Lynx Point-LP PCI Express Root Port 4
Rev:    e4
Driver:    pcieport

Device:    00:1c.4
Class:    PCI bridge
Vendor:    Intel Corporation
Device:    Lynx Point-LP PCI Express Root Port 5
Rev:    e4
Driver:    pcieport

Device:    00:1d.0
Class:    USB controller
Vendor:    Intel Corporation
Device:    Lynx Point-LP USB EHCI #1
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
ProgIf:    20
Driver:    ehci-pci

Device:    00:1f.0
Class:    ISA bridge
Vendor:    Intel Corporation
Device:    Lynx Point-LP LPC Controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
Driver:    lpc_ich

Device:    00:1f.2
Class:    SATA controller
Vendor:    Intel Corporation
Device:    Lynx Point-LP SATA Controller 1 [AHCI mode]
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04
ProgIf:    01
Driver:    ahci

Device:    00:1f.3
Class:    SMBus
Vendor:    Intel Corporation
Device:    Lynx Point-LP SMBus Controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    04

Device:    01:00.0
Class:    Ethernet controller
Vendor:    Realtek Semiconductor Co., Ltd.
Device:    RTL8101E/RTL8102E PCI Express Fast Ethernet controller
SVendor:    Dell
SDevice:    Device 05ea
Rev:    07
Driver:    r8169

Device:    02:00.0
Class:    Network controller
Vendor:    Qualcomm Atheros
Device:    QCA9565 / AR9565 Wireless Network Adapter
SVendor:    Dell
SDevice:    Device 020c
Rev:    01
Driver:    ath9k

Device:    03:00.0
Class:    Display controller
Vendor:    Advanced Micro Devices, Inc. [AMD/ATI]
Device:    Sun XT [Radeon HD 8670A/8670M/8690M]
SVendor:    Dell
SDevice:    Device 05ea
Driver:    fglrx_pci
```

I eventually managed to get it to create an xorg.conf which also identifies the driver, however trying to start X keeps generating the dreaded "Server terminated with error (1)" and no display detected. 

Xorg.conf (some have suggested changing the 'device' line. I have tried 'fglrx', 'ati', 'ati_pci', doesn't help) -

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx_pci"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

Xorg.1.log -

```
[  1403.791] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[  1403.792] X Protocol Version 11, Revision 0
[  1403.792] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  1403.793] Current Operating System: Linux the-patriarchy 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64
[  1403.793] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic.efi.signed root=UUID=9152932a-5ba8-4fec-befc-a23f544c0f6c ro quiet splash vt.handoff=7
[  1403.794] Build Date: 17 December 2013  10:06:15AM
[  1403.794] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[  1403.795] Current version of pixman: 0.30.2
[  1403.796]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1403.796] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1403.798] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Feb  8 12:03:03 2014
[  1403.799] (==) Using config file: "/etc/X11/xorg.conf"
[  1403.800] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1403.800] (==) ServerLayout "aticonfig Layout"
[  1403.800] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[  1403.800] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[  1403.800] (**) |   |-->Device "aticonfig-Device[0]-0"
[  1403.800] (==) Automatically adding devices
[  1403.800] (==) Automatically enabling devices
[  1403.800] (==) Automatically adding GPU devices
[  1403.800] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1403.800]     Entry deleted from font path.
[  1403.800] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1403.800]     Entry deleted from font path.
[  1403.800] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1403.800]     Entry deleted from font path.
[  1403.800] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1403.800]     Entry deleted from font path.
[  1403.800] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1403.800]     Entry deleted from font path.
[  1403.800] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1403.800] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1403.800] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1403.800] (II) Loader magic: 0x7f7b3acf0d20
[  1403.800] (II) Module ABI versions:
[  1403.800]     X.Org ANSI C Emulation: 0.4
[  1403.800]     X.Org Video Driver: 14.1
[  1403.800]     X.Org XInput driver : 19.1
[  1403.800]     X.Org Server Extension : 7.0
[  1403.800] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1403.801] (--) PCI:*(0:0:2:0) 8086:0a16:1028:05ea rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005000/64
[  1403.801] (--) PCI: (0:3:0:0) 1002:6660:1028:05ea rev 0, Mem @ 0xa0000000/268435456, 0xc0500000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[  1403.801] (II) Open ACPI successful (/var/run/acpid.socket)
[  1403.802] Initializing built-in extension Generic Event Extension
[  1403.803] Initializing built-in extension SHAPE
[  1403.803] Initializing built-in extension MIT-SHM
[  1403.804] Initializing built-in extension XInputExtension
[  1403.804] Initializing built-in extension XTEST
[  1403.805] Initializing built-in extension BIG-REQUESTS
[  1403.806] Initializing built-in extension SYNC
[  1403.806] Initializing built-in extension XKEYBOARD
[  1403.807] Initializing built-in extension XC-MISC
[  1403.807] Initializing built-in extension SECURITY
[  1403.808] Initializing built-in extension XINERAMA
[  1403.809] Initializing built-in extension XFIXES
[  1403.809] Initializing built-in extension RENDER
[  1403.810] Initializing built-in extension RANDR
[  1403.810] Initializing built-in extension COMPOSITE
[  1403.811] Initializing built-in extension DAMAGE
[  1403.811] Initializing built-in extension MIT-SCREEN-SAVER
[  1403.812] Initializing built-in extension DOUBLE-BUFFER
[  1403.812] Initializing built-in extension RECORD
[  1403.813] Initializing built-in extension DPMS
[  1403.813] Initializing built-in extension X-Resource
[  1403.814] Initializing built-in extension XVideo
[  1403.815] Initializing built-in extension XVideo-MotionCompensation
[  1403.815] Initializing built-in extension SELinux
[  1403.816] Initializing built-in extension XFree86-VidModeExtension
[  1403.816] Initializing built-in extension XFree86-DGA
[  1403.817] Initializing built-in extension XFree86-DRI
[  1403.817] Initializing built-in extension DRI2
[  1403.817] (II) "glx" will be loaded by default.
[  1403.817] (WW) "xmir" is not to be loaded by default. Skipping.
[  1403.817] (II) LoadModule: "glx"
[  1403.817] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1403.818] (II) Module glx: vendor="X.Org Foundation"
[  1403.818]     compiled for 1.14.5, module version = 1.0.0
[  1403.818]     ABI class: X.Org Server Extension, version 7.0
[  1403.818] (==) AIGLX enabled
[  1403.818] Loading extension GLX
[  1403.818] (II) LoadModule: "fglrxpci"
[  1403.818] (WW) Warning, couldn't open module fglrxpci
[  1403.818] (II) UnloadModule: "fglrxpci"
[  1403.818] (II) Unloading fglrxpci
[  1403.818] (EE) Failed to load module "fglrxpci" (module does not exist, 0)
[  1403.818] (==) Matched intel as autoconfigured driver 0
[  1403.818] (==) Matched intel as autoconfigured driver 1
[  1403.818] (==) Matched vesa as autoconfigured driver 2
[  1403.818] (==) Matched modesetting as autoconfigured driver 3
[  1403.818] (==) Matched fbdev as autoconfigured driver 4
[  1403.818] (==) Assigned the driver to the xf86ConfigLayout
[  1403.818] (II) LoadModule: "intel"
[  1403.818] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1403.819] (II) Module intel: vendor="X.Org Foundation"
[  1403.819]     compiled for 1.14.5, module version = 2.99.909
[  1403.819]     Module class: X.Org Video Driver
[  1403.819]     ABI class: X.Org Video Driver, version 14.1
[  1403.819] (II) LoadModule: "vesa"
[  1403.819] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1403.819] (II) Module vesa: vendor="X.Org Foundation"
[  1403.819]     compiled for 1.14.1, module version = 2.3.2
[  1403.819]     Module class: X.Org Video Driver
[  1403.819]     ABI class: X.Org Video Driver, version 14.1
[  1403.819] (II) LoadModule: "modesetting"
[  1403.819] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1403.819] (II) Module modesetting: vendor="X.Org Foundation"
[  1403.819]     compiled for 1.14.1, module version = 0.8.0
[  1403.819]     Module class: X.Org Video Driver
[  1403.819]     ABI class: X.Org Video Driver, version 14.1
[  1403.819] (II) LoadModule: "fbdev"
[  1403.819] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1403.819] (II) Module fbdev: vendor="X.Org Foundation"
[  1403.819]     compiled for 1.14.1, module version = 0.4.3
[  1403.819]     Module class: X.Org Video Driver
[  1403.819]     ABI class: X.Org Video Driver, version 14.1
[  1403.819] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  1403.819] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[  1403.819] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[  1403.819] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[  1403.819] (II) VESA: driver for VESA chipsets: vesa
[  1403.819] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1403.819] (II) FBDEV: driver for framebuffer: fbdev
[  1403.819] (--) using VT number 8

[  1403.822] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.909+git20140206.823382d2-0ubuntu0sarvatt~saucy (Robert Hooker <sarvatt@ubuntu.com>)
[  1403.822] (WW) Falling back to old probe method for vesa
[  1403.823] (WW) Falling back to old probe method for modesetting
[  1403.823] (WW) Falling back to old probe method for fbdev
[  1403.823] (II) Loading sub module "fbdevhw"
[  1403.823] (II) LoadModule: "fbdevhw"
[  1403.823] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1403.823] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1403.823]     compiled for 1.14.5, module version = 0.0.2
[  1403.823]     ABI class: X.Org Video Driver, version 14.1
[  1403.823] (EE) Screen 0 deleted because of no matching config section.
[  1403.823] (II) UnloadModule: "modesetting"
[  1403.823] (EE) Device(s) detected, but none match those in the config file.
[  1403.823] (EE) 
Fatal server error:
[  1403.823] (EE) no screens found(EE) 
[  1403.823] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  1403.823] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[  1403.823] (EE) 
[  1403.829] (EE) Server terminated with error (1). Closing log file.
```

This is the most disgusting linux experience I have ever had. What am I missing? Has anybody gotten this card to work? Basically, if I don't fix this this weekend, I'm getting a refund for the machine.

Footnote: live cd sessions fail to load with the same problems as the installation. Yes, I have tried 14.04 beta - exactly the same.

[SIZE=3]**Update: **[/SIZE]

I have found a reliable (as opposed to random) way to get to a login screen. Replace the contents of xorg.conf with just -

```
Section "Device"
 Identifier "ATI radeon 6870"
 Driver "fglrx"
EndSection
```

as per -

[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)

Login is accepted OK, but then there's a black screen and an uninformative error window that wants to report to Canonical. I have no idea where the error details can be found. Trying to invoke ***fglxrinfo*** just gives **Error: unable to open display (null)**. This is the content of the new Xorg log -

```
[    15.543] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    15.543] X Protocol Version 11, Revision 0
[    15.543] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    15.543] Current Operating System: Linux the-patriarchy 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64
[    15.543] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic.efi.signed root=UUID=9152932a-5ba8-4fec-befc-a23f544c0f6c ro quiet splash vt.handoff=7
[    15.543] Build Date: 17 December 2013  10:06:15AM
[    15.543] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    15.543] Current version of pixman: 0.30.2
[    15.543]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.543] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.543] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  8 18:20:27 2014
[    15.555] (==) Using config file: "/etc/X11/xorg.conf"
[    15.555] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.586] (==) No Layout section.  Using the first Screen section.
[    15.586] (==) No screen section available. Using defaults.
[    15.586] (**) |-->Screen "Default Screen Section" (0)
[    15.586] (**) |   |-->Monitor "<default monitor>"
[    15.586] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    15.586] (**) |   |-->Device "ATI radeon 6870"
[    15.586] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    15.586] (==) Automatically adding devices
[    15.586] (==) Automatically enabling devices
[    15.586] (==) Automatically adding GPU devices
[    15.586] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.586]     Entry deleted from font path.
[    15.586] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.586]     Entry deleted from font path.
[    15.586] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.586]     Entry deleted from font path.
[    15.586] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.586]     Entry deleted from font path.
[    15.586] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.586]     Entry deleted from font path.
[    15.586] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.586] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.586] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.586] (II) Loader magic: 0x7f13bf9f3d20
[    15.586] (II) Module ABI versions:
[    15.586]     X.Org ANSI C Emulation: 0.4
[    15.586]     X.Org Video Driver: 14.1
[    15.586]     X.Org XInput driver : 19.1
[    15.586]     X.Org Server Extension : 7.0
[    15.586] (II) xfree86: Adding drm device (/dev/dri/card0)
[    15.587] (--) PCI:*(0:0:2:0) 8086:0a16:1028:05ea rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005000/64
[    15.588] (--) PCI: (0:3:0:0) 1002:6660:1028:05ea rev 0, Mem @ 0xa0000000/268435456, 0xc0500000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    15.588] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.588] Initializing built-in extension Generic Event Extension
[    15.588] Initializing built-in extension SHAPE
[    15.588] Initializing built-in extension MIT-SHM
[    15.588] Initializing built-in extension XInputExtension
[    15.588] Initializing built-in extension XTEST
[    15.588] Initializing built-in extension BIG-REQUESTS
[    15.588] Initializing built-in extension SYNC
[    15.588] Initializing built-in extension XKEYBOARD
[    15.588] Initializing built-in extension XC-MISC
[    15.588] Initializing built-in extension SECURITY
[    15.588] Initializing built-in extension XINERAMA
[    15.588] Initializing built-in extension XFIXES
[    15.588] Initializing built-in extension RENDER
[    15.588] Initializing built-in extension RANDR
[    15.588] Initializing built-in extension COMPOSITE
[    15.588] Initializing built-in extension DAMAGE
[    15.588] Initializing built-in extension MIT-SCREEN-SAVER
[    15.588] Initializing built-in extension DOUBLE-BUFFER
[    15.588] Initializing built-in extension RECORD
[    15.588] Initializing built-in extension DPMS
[    15.588] Initializing built-in extension X-Resource
[    15.588] Initializing built-in extension XVideo
[    15.588] Initializing built-in extension XVideo-MotionCompensation
[    15.588] Initializing built-in extension SELinux
[    15.588] Initializing built-in extension XFree86-VidModeExtension
[    15.588] Initializing built-in extension XFree86-DGA
[    15.588] Initializing built-in extension XFree86-DRI
[    15.588] Initializing built-in extension DRI2
[    15.588] (II) "glx" will be loaded by default.
[    15.588] (WW) "xmir" is not to be loaded by default. Skipping.
[    15.588] (II) LoadModule: "dri2"
[    15.588] (II) Module "dri2" already built-in
[    15.588] (II) LoadModule: "glamoregl"
[    15.646] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    16.213] (II) Module glamoregl: vendor="X.Org Foundation"
[    16.213]     compiled for 1.14.5, module version = 0.5.1
[    16.213]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.213] (II) LoadModule: "glx"
[    16.213] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.213] (II) Module glx: vendor="X.Org Foundation"
[    16.213]     compiled for 1.14.5, module version = 1.0.0
[    16.213]     ABI class: X.Org Server Extension, version 7.0
[    16.213] (==) AIGLX enabled
[    16.213] Loading extension GLX
[    16.213] (II) LoadModule: "fglrx"
[    16.213] (WW) Warning, couldn't open module fglrx
[    16.213] (II) UnloadModule: "fglrx"
[    16.213] (II) Unloading fglrx
[    16.213] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.213] (==) Matched intel as autoconfigured driver 0
[    16.213] (==) Matched intel as autoconfigured driver 1
[    16.213] (==) Matched vesa as autoconfigured driver 2
[    16.213] (==) Matched modesetting as autoconfigured driver 3
[    16.213] (==) Matched fbdev as autoconfigured driver 4
[    16.213] (==) Assigned the driver to the xf86ConfigLayout
[    16.213] (II) LoadModule: "intel"
[    16.214] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.237] (II) Module intel: vendor="X.Org Foundation"
[    16.237]     compiled for 1.14.5, module version = 2.99.909
[    16.237]     Module class: X.Org Video Driver
[    16.237]     ABI class: X.Org Video Driver, version 14.1
[    16.237] (II) LoadModule: "vesa"
[    16.238] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.238] (II) Module vesa: vendor="X.Org Foundation"
[    16.238]     compiled for 1.14.1, module version = 2.3.2
[    16.238]     Module class: X.Org Video Driver
[    16.238]     ABI class: X.Org Video Driver, version 14.1
[    16.238] (II) LoadModule: "modesetting"
[    16.238] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.238] (II) Module modesetting: vendor="X.Org Foundation"
[    16.238]     compiled for 1.14.1, module version = 0.8.0
[    16.238]     Module class: X.Org Video Driver
[    16.238]     ABI class: X.Org Video Driver, version 14.1
[    16.238] (II) LoadModule: "fbdev"
[    16.238] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.238] (II) Module fbdev: vendor="X.Org Foundation"
[    16.238]     compiled for 1.14.1, module version = 0.4.3
[    16.238]     Module class: X.Org Video Driver
[    16.238]     ABI class: X.Org Video Driver, version 14.1
[    16.238] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    16.239] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    16.239] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    16.239] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    16.239] (II) VESA: driver for VESA chipsets: vesa
[    16.239] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.239] (II) FBDEV: driver for framebuffer: fbdev
[    16.239] (++) using VT number 7

[    16.239] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.909+git20140206.823382d2-0ubuntu0sarvatt~saucy (Robert Hooker <sarvatt@ubuntu.com>)
[    16.239] (WW) Falling back to old probe method for vesa
[    16.239] (WW) Falling back to old probe method for modesetting
[    16.239] (WW) Falling back to old probe method for fbdev
[    16.239] (II) Loading sub module "fbdevhw"
[    16.239] (II) LoadModule: "fbdevhw"
[    16.239] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.239] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.239]     compiled for 1.14.5, module version = 0.0.2
[    16.239]     ABI class: X.Org Video Driver, version 14.1
[    16.239] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[    16.239] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    16.239] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    16.239] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.239] (==) intel(0): RGB weight 888
[    16.239] (==) intel(0): Default visual is TrueColor
[    16.240] (**) intel(0): Framebuffer tiled
[    16.240] (**) intel(0): Pixmaps tiled
[    16.240] (**) intel(0): "Tear free" disabled
[    16.240] (**) intel(0): Forcing per-crtc-pixmaps? no
[    16.240] (II) intel(0): Output eDP1 has no monitor section
[    16.240] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    16.240] (II) intel(0): Output DP1 has no monitor section
[    16.240] (II) intel(0): Output HDMI1 has no monitor section
[    16.240] (II) intel(0): Output DP2 has no monitor section
[    16.240] (II) intel(0): Output HDMI2 has no monitor section
[    16.240] (II) intel(0): Output VIRTUAL1 has no monitor section
[    16.240] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[    16.240] (==) intel(0): DPI set to (96, 96)
[    16.240] (II) Loading sub module "dri2"
[    16.240] (II) LoadModule: "dri2"
[    16.240] (II) Module "dri2" already built-in
[    16.240] (II) UnloadModule: "vesa"
[    16.240] (II) Unloading vesa
[    16.240] (II) UnloadModule: "modesetting"
[    16.240] (II) Unloading modesetting
[    16.240] (II) UnloadModule: "fbdev"
[    16.240] (II) Unloading fbdev
[    16.240] (II) UnloadSubModule: "fbdevhw"
[    16.240] (II) Unloading fbdevhw
[    16.240] (==) Depth 24 pixmap format is 32 bpp
[    16.261] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    16.261] (==) intel(0): Backing store disabled
[    16.261] (==) intel(0): Silken mouse enabled
[    16.261] (II) intel(0): HW Cursor enabled
[    16.261] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.261] (==) intel(0): DPMS enabled
[    16.261] (II) intel(0): [DRI2] Setup complete
[    16.261] (II) intel(0): [DRI2]   DRI driver: i965
[    16.261] (II) intel(0): [DRI2]   VDPAU driver: i965
[    16.261] (II) intel(0): direct rendering: DRI2 Enabled
[    16.261] (==) intel(0): hotplug detection: "enabled"
[    16.262] (--) RandR disabled
[    16.265] (II) SELinux: Disabled on system
[    16.367] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.367] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.367] (II) AIGLX: enabled GLX_ARB_create_context
[    16.367] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.367] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.367] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.367] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.367] (II) AIGLX: Loaded and initialized i965
[    16.367] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.369] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    16.388] (II) intel(0): Setting screen physical size to 361 x 203
[    16.403] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.417] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.417] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.417] (II) LoadModule: "evdev"
[    16.417] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.427] (II) Module evdev: vendor="X.Org Foundation"
[    16.427]     compiled for 1.14.1, module version = 2.7.3
[    16.427]     Module class: X.Org XInput Driver
[    16.427]     ABI class: X.Org XInput driver, version 19.1
[    16.427] (II) Using input driver 'evdev' for 'Power Button'
[    16.427] (**) Power Button: always reports core events
[    16.427] (**) evdev: Power Button: Device: "/dev/input/event2"
[    16.427] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.427] (--) evdev: Power Button: Found keys
[    16.427] (II) evdev: Power Button: Configuring as keyboard
[    16.427] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    16.427] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.427] (**) Option "xkb_rules" "evdev"
[    16.427] (**) Option "xkb_model" "pc105"
[    16.427] (**) Option "xkb_layout" "us"
[    16.428] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    16.428] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.428] (II) Using input driver 'evdev' for 'Video Bus'
[    16.428] (**) Video Bus: always reports core events
[    16.428] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    16.428] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.428] (--) evdev: Video Bus: Found keys
[    16.428] (II) evdev: Video Bus: Configuring as keyboard
[    16.428] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    16.428] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.428] (**) Option "xkb_rules" "evdev"
[    16.428] (**) Option "xkb_model" "pc105"
[    16.428] (**) Option "xkb_layout" "us"
[    16.428] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.428] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.428] (II) Using input driver 'evdev' for 'Power Button'
[    16.428] (**) Power Button: always reports core events
[    16.428] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.428] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.428] (--) evdev: Power Button: Found keys
[    16.428] (II) evdev: Power Button: Configuring as keyboard
[    16.428] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input1/event1"
[    16.428] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.428] (**) Option "xkb_rules" "evdev"
[    16.428] (**) Option "xkb_model" "pc105"
[    16.428] (**) Option "xkb_layout" "us"
[    16.429] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.429] (II) No input driver specified, ignoring this device.
[    16.429] (II) This device may have been added with another device file.
[    16.429] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    16.429] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.429] (II) Using input driver 'evdev' for 'Video Bus'
[    16.429] (**) Video Bus: always reports core events
[    16.429] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    16.429] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.429] (--) evdev: Video Bus: Found keys
[    16.429] (II) evdev: Video Bus: Configuring as keyboard
[    16.429] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f/LNXVIDEO:00/input/input7/event7"
[    16.429] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    16.429] (**) Option "xkb_rules" "evdev"
[    16.429] (**) Option "xkb_model" "pc105"
[    16.429] (**) Option "xkb_layout" "us"
[    16.429] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.429] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    16.429] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event10)
[    16.429] (II) No input driver specified, ignoring this device.
[    16.429] (II) This device may have been added with another device file.
[    16.429] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event11)
[    16.429] (II) No input driver specified, ignoring this device.
[    16.429] (II) This device may have been added with another device file.
[    16.430] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=8 (/dev/input/event9)
[    16.430] (II) No input driver specified, ignoring this device.
[    16.430] (II) This device may have been added with another device file.
[    16.430] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event12)
[    16.430] (II) No input driver specified, ignoring this device.
[    16.430] (II) This device may have been added with another device file.
[    16.430] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event4)
[    16.430] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    16.430] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    16.430] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    16.430] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event4"
[    16.430] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xc45 Product 0x649a
[    16.430] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    16.430] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    16.430] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.8/1-1.8:1.0/input/input4/event4"
[    16.430] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 10)
[    16.430] (**) Option "xkb_rules" "evdev"
[    16.430] (**) Option "xkb_model" "pc105"
[    16.430] (**) Option "xkb_layout" "us"
[    16.430] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.430] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.430] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.430] (**) AT Translated Set 2 keyboard: always reports core events
[    16.430] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.430] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.430] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.430] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.430] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    16.430] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    16.430] (**) Option "xkb_rules" "evdev"
[    16.430] (**) Option "xkb_model" "pc105"
[    16.430] (**) Option "xkb_layout" "us"
[    16.431] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    16.431] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.431] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.431] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    16.431] (II) LoadModule: "synaptics"
[    16.431] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.431] (II) Module synaptics: vendor="X.Org Foundation"
[    16.431]     compiled for 1.14.2, module version = 1.7.1
[    16.431]     Module class: X.Org XInput Driver
[    16.431]     ABI class: X.Org XInput driver, version 19.1
[    16.431] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.431] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.431] (**) Option "Device" "/dev/input/event6"
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5674 (res 44)
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754 (res 68)
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    16.452] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.452] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.464] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    16.464] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    16.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    16.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    16.464] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.464] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.464] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.464] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.466] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event5)
[    16.466] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    16.466] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    16.466] (**) Dell WMI hotkeys: always reports core events
[    16.466] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event5"
[    16.466] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    16.466] (--) evdev: Dell WMI hotkeys: Found keys
[    16.466] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    16.466] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    16.466] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    16.466] (**) Option "xkb_rules" "evdev"
[    16.466] (**) Option "xkb_model" "pc105"
[    16.466] (**) Option "xkb_layout" "us"
[    18.963] (II) intel(0): EDID vendor "SDC", prod id 21569
[    18.963] (II) intel(0): Printing DDC gathered Modelines:
[    18.963] (II) intel(0): Modeline "1366x768"x0.0   76.30  1366 1430 1478 1606  768 770 775 792 +hsync -vsync (47.5 kHz eP)
[    18.963] (II) intel(0): Modeline "1366x768"x0.0   50.80  1366 1430 1478 1606  768 770 775 792 +hsync -vsync (31.6 kHz e)
[    46.201] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    46.757] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    46.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   382.260] (II) AIGLX: Suspending AIGLX clients for VT switch
```

These bits seem important, but are meaningless to me and google isn't helpful either, but seem to point back inability to open a display -

```
The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[...]
[   382.260] (II) AIGLX: Suspending AIGLX clients for VT switch
```

Also contents of .xsessions-errors -

```
Segmentation fault (core dumped)
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (1734) terminated with status 1
Xsession: X session started for fnord at Sat Feb  8 23:42:29 EST 2014
localuser:fnord being added to access control list
Script for cjkv started at run_im.
Script for default started at run_im.
Unable to create /home/fnord/.dbus/session-bus
Script for cjkv started at run_im.
Script for default started at run_im.
gnome-session-is-accelerated: GL_MAX_{TEXTURE,RENDERBUFFER}_SIZE is too small.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: GL_MAX_{TEXTURE,RENDERBUFFER}_SIZE is too small.
gnome-session-check-accelerated: Helper exited with code 256

** (process:2240): WARNING **: software acceleration check failed: Child process exited with code 1

** (x-session-manager:2240): CRITICAL **: We failed, but the fail whale is dead. Sorry....
Xsession: X session started for fnord at Sat Feb  8 23:50:22 EST 2014
localuser:fnord being added to access control list
Script for cjkv started at run_im.
Script for default started at run_im.
Unable to create /home/fnord/.dbus/session-bus
Script for cjkv started at run_im.
Script for default started at run_im.
gnome-session-is-accelerated: GL_MAX_{TEXTURE,RENDERBUFFER}_SIZE is too small.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: GL_MAX_{TEXTURE,RENDERBUFFER}_SIZE is too small.
gnome-session-check-accelerated: Helper exited with code 256

** (process:2338): WARNING **: software acceleration check failed: Child process exited with code 1

** (x-session-manager:2338): CRITICAL **: We failed, but the fail whale is dead. Sorry....
```

I'm totally lost here and can't believe I am the only one out there that's run into this brick wall.

---

### Post by felgro on 2014-02-09
Thanks for the deafening response - same as everywhere else, no one has any idea. I hate these cards with a passion - especially when this particular Dell is "approved" hardware. Anyway, I found a workable fix -

* Use Ubuntu 14.04 alpha - you will only be able to access a terminal
* Use the beta AMD driver
* Follow the procedure to prep the machine to make .deb install packs at -

[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

- just modify package by using: 

```
sudo ./amd-driver-installer-13.35.1005-x86.x86_64.run --buildpkg Ubuntu/trusty
```

to build them. Check X is still alive, reboot, drop down to terminal (you won't have Unity working yet) and run -

```
sudo amdconfig --initial -f
```

Reboot. You should be able to log into Unity. One weirdness I have is the initial login screen won't accept any keyboard input. If you get that, select "guest login", then switch back to your account and you should be able to login.

---

### Post by StuartN on 2014-03-14
I just received my Lenovo S540 with the same chipset (Intel Haswell-ULT Integrated Graphics + Radeon HD 8670A/8670M/8690M) and had the same difficulties.

I did a full update (sudo apt-get update, sudo apt-get dist-upgrade) and installed Gnome (sudo apt-get install gnome), selecting GDM as the display manager. I then logged out and selected Gnome as my desktop manager.

Now I have a beautiful HD display and fully functioning login, without installing the proprietary drivers yet - I am not sure if there is a benefit in terms of power consumption or performance.

---

### Post by StuartN on 2014-03-14
I just received my Lenovo S540 with the same chipset (Intel Haswell-ULT Integrated Graphics + Radeon HD 8670A/8670M/8690M) and had the same difficulties.

I did a full update (sudo apt-get update, sudo apt-get dist-upgrade) and installed Gnome (sudo apt-get install gnome), selecting GDM as the display manager. I then logged out and selected Gnome as my desktop manager.

Now I have a beautiful HD display and fully functioning login, without installing the proprietary drivers yet - I am not sure if there is a benefit in terms of power consumption or performance.

---

### Post by StuartN on 2014-03-21
Ubuntu 14.04 was not stable, it would not start a graphical interface from cold.

Now using Ubuntu 12.04 with the proprietary Hydravision experimental Beta driver that Ubuntu suggests under Additional Drivers. I switched to the Intel integrated display and have had no problems at all, with booting from cold, restarting and resuming from suspend.

---

