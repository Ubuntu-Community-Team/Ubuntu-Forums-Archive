---
title: "Can't get dual GPUs to work (AMD 6950 + AMD 6450)"
date: 2014-10-29
forum: Multimedia Software
---

### Post by asura2 on 2014-10-29
Hey guys! Having a bit of problem configuring my GPUs. I've always had no problem setting up dual monitors, but recently I got a 6450 as I figured I'd get another monitor soon for 3 all together. Right now I'm running one monitor per card. Everything works flawlessly with the FOSS drivers, but I don't get the speed or power with games and other things that I should, not to mention no access to using my GPU for anything else.

Here are my current issues:

1. I use Cinnamon from a PPA. Not an issue as I can always change to something else. If use the AMD Control Center to enable the monitor on the 6450, Cinnamon will no longer boot as it just keeps crashing.
2. Using GNOME and others, I can get to my desktop just fine. Here's the major issue. The second monitor is on, but showing nothing, and I can scroll too it. I figured multidisplay or Xinerama would fix it. Xinerama just causes a black screen overall, and I have no other options than single display in AMD Control Center. Cloning doesn't work either. Just full black screen for both monitors regardless of which way I go, but it does show them "on", as in they don't go to sleep or power down.

I have tried the following:
- aticonfig with adapters and heads settings
- normal gksu amdcccle adjustment attempts
- modifying my xorg.conf with things like EnableRandR12

I'm not sure where else to go at this point, figured I'd finally ask for some assistance. I'm running Ubuntu Minimal x64.

Xorg Config is below in code box. I will also do some more attempts and post if I make any progress. Thanks for any help you can give.

```
Section "ServerLayout"    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[1]-0" 0 0
    Screen         "aticonfig-Screen[0]-0" 1920 0
    Option        "Clone" "false"
    Option        "Xinerama" "0"
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection


Section "Monitor"
    Identifier   "1-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-Default monitor" "1-Default monitor"
    BusID       "PCI:1:0:0"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:2:0:0"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```


-- EDIT --
Xorg.0.log for when Xinerama is enabled. Used CTRL+ALT+F1 to get to console to get it.

```
[    15.108] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    15.108] X Protocol Version 11, Revision 0
[    15.108] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    15.108] Current Operating System: Linux 7A65726F 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    15.108] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=7d334e21-f7ce-4a29-9405-1a31786ae0e1 ro splash quiet vt.handoff=7
[    15.108] Build Date: 30 July 2014  12:21:54AM
[    15.108] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    15.108] Current version of pixman: 0.30.2
[    15.108] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.108] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.108] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 29 10:08:26 2014
[    15.109] (==) Using config file: "/etc/X11/xorg.conf"
[    15.109] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.109] (==) ServerLayout "aticonfig Layout"
[    15.109] (**) |-->Screen "aticonfig-Screen[1]-0" (0)
[    15.109] (**) |   |-->Monitor "<default monitor>"
[    15.109] (**) |   |-->Device "aticonfig-Device[1]-0"
[    15.109] (==) No monitor specified for screen "aticonfig-Screen[1]-0".
	Using a default monitor configuration.
[    15.109] (**) |-->Screen "aticonfig-Screen[0]-0" (1)
[    15.109] (**) |   |-->Monitor "<default monitor>"
[    15.109] (**) |   |-->Device "aticonfig-Device[0]-0"
[    15.109] (==) No monitor specified for screen "aticonfig-Screen[0]-0".
	Using a default monitor configuration.
[    15.109] (**) Option "Xinerama" "on"
[    15.109] (==) Automatically adding devices
[    15.109] (==) Automatically enabling devices
[    15.109] (==) Automatically adding GPU devices
[    15.109] (**) Xinerama: enabled
[    15.109] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.109] 	Entry deleted from font path.
[    15.109] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.109] 	Entry deleted from font path.
[    15.109] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.109] 	Entry deleted from font path.
[    15.109] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.109] 	Entry deleted from font path.
[    15.109] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.109] 	Entry deleted from font path.
[    15.109] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    15.109] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.109] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.109] (II) Loader magic: 0x7f0bec28bd40
[    15.109] (II) Module ABI versions:
[    15.109] 	X.Org ANSI C Emulation: 0.4
[    15.109] 	X.Org Video Driver: 15.0
[    15.109] 	X.Org XInput driver : 20.0
[    15.109] 	X.Org Server Extension : 8.0
[    15.111] (--) PCI:*(0:1:0:0) 1002:6779:174b:e206 rev 0, Mem @ 0xc0000000/268435456, 0xfdcc0000/131072, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[    15.111] (--) PCI: (0:2:0:0) 1002:6719:174b:186b rev 0, Mem @ 0xd0000000/268435456, 0xfdbc0000/131072, I/O @ 0x0000be00/256, BIOS @ 0x????????/131072
[    15.111] Initializing built-in extension Generic Event Extension
[    15.111] Initializing built-in extension SHAPE
[    15.111] Initializing built-in extension MIT-SHM
[    15.111] Initializing built-in extension XInputExtension
[    15.111] Initializing built-in extension XTEST
[    15.111] Initializing built-in extension BIG-REQUESTS
[    15.111] Initializing built-in extension SYNC
[    15.111] Initializing built-in extension XKEYBOARD
[    15.111] Initializing built-in extension XC-MISC
[    15.111] Initializing built-in extension SECURITY
[    15.111] Initializing built-in extension XINERAMA
[    15.111] Initializing built-in extension XFIXES
[    15.111] Initializing built-in extension RENDER
[    15.111] Initializing built-in extension RANDR
[    15.111] Initializing built-in extension COMPOSITE
[    15.111] Initializing built-in extension DAMAGE
[    15.111] Initializing built-in extension MIT-SCREEN-SAVER
[    15.111] Initializing built-in extension DOUBLE-BUFFER
[    15.111] Initializing built-in extension RECORD
[    15.111] Initializing built-in extension DPMS
[    15.111] Initializing built-in extension Present
[    15.111] Initializing built-in extension DRI3
[    15.111] Initializing built-in extension X-Resource
[    15.111] Initializing built-in extension XVideo
[    15.111] Initializing built-in extension XVideo-MotionCompensation
[    15.111] Initializing built-in extension SELinux
[    15.111] Initializing built-in extension XFree86-VidModeExtension
[    15.111] Initializing built-in extension XFree86-DGA
[    15.111] Initializing built-in extension XFree86-DRI
[    15.111] Initializing built-in extension DRI2
[    15.111] (II) "glx" will be loaded by default.
[    15.111] (WW) "xmir" is not to be loaded by default. Skipping.
[    15.111] (II) LoadModule: "glx"
[    15.111] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    15.112] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    15.112] 	compiled for 6.9.0, module version = 1.0.0
[    15.112] Loading extension GLX
[    15.112] (II) LoadModule: "fglrx"
[    15.112] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    15.130] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    15.130] 	compiled for 1.4.99.906, module version = 13.35.5
[    15.130] 	Module class: X.Org Video Driver
[    15.130] (II) Loading sub module "fglrxdrm"
[    15.130] (II) LoadModule: "fglrxdrm"
[    15.130] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    15.131] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    15.131] 	compiled for 1.4.99.906, module version = 13.35.5
[    15.131] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
[    15.131] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
[    15.131] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
[    15.131] (++) using VT number 7


[    15.131] (WW) Falling back to old probe method for fglrx
[    15.139] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    15.152] ukiDynamicMajor: found major device number 250
[    15.152] ukiDynamicMajor: found major device number 250
[    15.152] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    15.152] ukiOpenDevice: node name is /dev/ati/card0
[    15.152] ukiOpenDevice: open result is 9, (OK)
[    15.352] ukiOpenByBusid: ukiOpenMinor returns 9
[    15.352] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.352] ukiOpenDevice: node name is /dev/ati/card1
[    15.748] ukiOpenDevice: open result is 9, (OK)
[    15.748] ukiOpenByBusid: ukiOpenMinor returns 9
[    15.748] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.768] ukiDynamicMajor: found major device number 250
[    15.768] ukiDynamicMajor: found major device number 250
[    15.768] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.768] ukiOpenDevice: node name is /dev/ati/card0
[    15.768] ukiOpenDevice: open result is 9, (OK)
[    15.768] ukiOpenByBusid: ukiOpenMinor returns 9
[    15.768] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.801] (--) Chipset Supported AMD Graphics Processor (0x6779) found
[    15.801] (--) Chipset Supported AMD Graphics Processor (0x6719) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:3:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    15.801] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    15.801] (II) fglrx(0): pEnt->device->identifier=0x7f0bee16d370
[    15.801] (II) fglrx(1): pEnt->device->identifier=0x7f0bee16d6f0
[    15.802] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    15.802] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    15.802] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.802] (==) fglrx(0): Default visual is TrueColor
[    15.802] (==) fglrx(0): RGB weight 888
[    15.802] (II) fglrx(0): Using 8 bits per RGB 
[    15.802] (==) fglrx(0): Buffer Tiling is ON
[    15.802] (II) Loading sub module "fglrxdrm"
[    15.802] (II) LoadModule: "fglrxdrm"
[    15.802] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    15.803] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    15.803] 	compiled for 1.4.99.906, module version = 13.35.5
[    15.816] ukiDynamicMajor: found major device number 250
[    15.816] ukiDynamicMajor: found major device number 250
[    15.816] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    15.816] ukiOpenDevice: node name is /dev/ati/card0
[    15.816] ukiOpenDevice: open result is 11, (OK)
[    15.816] ukiOpenByBusid: ukiOpenMinor returns 11
[    15.816] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.816] ukiOpenDevice: node name is /dev/ati/card1
[    15.816] ukiOpenDevice: open result is 11, (OK)
[    15.816] ukiOpenByBusid: ukiOpenMinor returns 11
[    15.816] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.816] (**) fglrx(0): NoAccel = NO
[    15.816] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    15.816] (--) fglrx(0): Chipset: "AMD Radeon HD 6900 Series " (Chipset = 0x6719)
[    15.816] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x186b)
[    15.816] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    15.816] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    15.816] (--) fglrx(0): MMIO registers at 0xfdbc0000
[    15.816] (--) fglrx(0): I/O port at 0x0000be00
[    15.816] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    15.816] (II) fglrx(0): AC Adapter is used
[    15.817] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    15.817] (--) fglrx(0): Video RAM: 2097152 kByte, Type: GDDR5
[    15.817] (II) fglrx(0): PCIE card detected
[    15.817] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    15.817] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    15.817] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf800000000, MCFBSize = 0x80000000)
[    15.817] (II) fglrx(0): RandR 1.2 support is enabled!
[    15.817] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    15.817] (II) Loading sub module "fb"
[    15.817] (II) LoadModule: "fb"
[    15.818] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.818] (II) Module fb: vendor="X.Org Foundation"
[    15.818] 	compiled for 1.15.1, module version = 1.0.0
[    15.818] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.818] (II) fglrx(0): EDID Management option: EDID Management is enabled
[    15.818] (II) Loading sub module "ddc"
[    15.818] (II) LoadModule: "ddc"
[    15.818] (II) Module "ddc" already built-in
[    15.974] (II) fglrx(0): Output DFP1 has no monitor section
[    15.974] (II) fglrx(0): Output DFP2 has no monitor section
[    15.974] (II) fglrx(0): Output DFP3 has no monitor section
[    15.974] (II) fglrx(0): Output DFP4 has no monitor section
[    15.974] (II) fglrx(0): Output DFP5 using monitor section 0-DFP5
[    15.974] (**) fglrx(0): Option "PreferredMode" "1920x1080"
[    15.974] (**) fglrx(0): Option "Position" "0 0"
[    15.974] (**) fglrx(0): Option "Disable" "false"
[    15.974] (**) fglrx(0): Option "Rotate" "normal"
[    15.974] (**) fglrx(0): Option "TargetRefresh" "60"
[    15.974] (II) fglrx(0): Output DFP6 has no monitor section
[    15.974] (II) fglrx(0): Output DFP7 has no monitor section
[    15.974] (II) fglrx(0): Output CRT1 has no monitor section
[    15.974] (II) Loading sub module "ddc"
[    15.974] (II) LoadModule: "ddc"
[    15.974] (II) Module "ddc" already built-in
[    15.974] (II) fglrx(0): Connected Display0: DFP5
[    15.974] (II) fglrx(0): Display0 EDID data ---------------------------
[    15.974] (II) fglrx(0): Manufacturer: SAM  Model: b43  Serial#: 808662328
[    15.974] (II) fglrx(0): Year: 2014  Week: 24
[    15.974] (II) fglrx(0): EDID Version: 1.3
[    15.974] (II) fglrx(0): Digital Display Input
[    15.974] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    15.974] (II) fglrx(0): Gamma: 2.20
[    15.974] (II) fglrx(0): DPMS capabilities: Off
[    15.974] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.974] (II) fglrx(0): First detailed timing is preferred mode
[    15.974] (II) fglrx(0): redX: 0.646 redY: 0.333   greenX: 0.315 greenY: 0.620
[    15.974] (II) fglrx(0): blueX: 0.151 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[    15.974] (II) fglrx(0): Supported established timings:
[    15.974] (II) fglrx(0): 720x400@70Hz
[    15.974] (II) fglrx(0): 640x480@60Hz
[    15.974] (II) fglrx(0): 640x480@67Hz
[    15.974] (II) fglrx(0): 640x480@72Hz
[    15.975] (II) fglrx(0): 640x480@75Hz
[    15.975] (II) fglrx(0): 800x600@56Hz
[    15.975] (II) fglrx(0): 800x600@60Hz
[    15.975] (II) fglrx(0): 800x600@72Hz
[    15.975] (II) fglrx(0): 800x600@75Hz
[    15.975] (II) fglrx(0): 832x624@75Hz
[    15.975] (II) fglrx(0): 1024x768@60Hz
[    15.975] (II) fglrx(0): 1024x768@70Hz
[    15.975] (II) fglrx(0): 1024x768@75Hz
[    15.975] (II) fglrx(0): 1280x1024@75Hz
[    15.975] (II) fglrx(0): 1152x864@75Hz
[    15.975] (II) fglrx(0): Manufacturer's mask: 0
[    15.975] (II) fglrx(0): Supported standard timings:
[    15.975] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.975] (II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.975] (II) fglrx(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.975] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.975] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.975] (II) fglrx(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    15.975] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.975] (II) fglrx(0): Supported detailed timing:
[    15.975] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    15.975] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.975] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.975] (II) fglrx(0): Supported detailed timing:
[    15.975] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    15.975] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    15.975] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.975] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    15.975] (II) fglrx(0): Monitor name: S24D300
[    15.975] (II) fglrx(0): Supported detailed timing:
[    15.975] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    15.975] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    15.975] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.975] (II) fglrx(0): Supported detailed timing:
[    15.975] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    15.975] (II) fglrx(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    15.975] (II) fglrx(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    15.975] (II) fglrx(0): Supported detailed timing:
[    15.975] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    15.975] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    15.975] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    15.975] (II) fglrx(0): Number of EDID sections to follow: 1
[    15.975] (II) fglrx(0): EDID (in hex):
[    15.975] (II) fglrx(0): 	00ffffffffffff004c2d430b38353330
[    15.975] (II) fglrx(0): 	1818010380351e782a9ff5a555509e26
[    15.975] (II) fglrx(0): 	105054bfef80714f81c0810081809500
[    15.975] (II) fglrx(0): 	a9c0b3000101023a801871382d40582c
[    15.975] (II) fglrx(0): 	4500132b2100001e011d007251d01e20
[    15.975] (II) fglrx(0): 	6e285500132b2100001e000000fd0032
[    15.975] (II) fglrx(0): 	4b1e5111000a202020202020000000fc
[    15.975] (II) fglrx(0): 	00533234443330300a2020202020018a
[    15.975] (II) fglrx(0): End of Display0 EDID data --------------------
[    15.975] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    15.976] (II) fglrx(0): EDID for output DFP1
[    15.976] (II) fglrx(0): EDID for output DFP2
[    15.976] (II) fglrx(0): EDID for output DFP3
[    15.976] (II) fglrx(0): EDID for output DFP4
[    15.976] (II) fglrx(0): EDID for output DFP5
[    15.976] (II) fglrx(0): Manufacturer: SAM  Model: b43  Serial#: 808662328
[    15.976] (II) fglrx(0): Year: 2014  Week: 24
[    15.976] (II) fglrx(0): EDID Version: 1.3
[    15.976] (II) fglrx(0): Digital Display Input
[    15.976] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    15.976] (II) fglrx(0): Gamma: 2.20
[    15.976] (II) fglrx(0): DPMS capabilities: Off
[    15.976] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.976] (II) fglrx(0): First detailed timing is preferred mode
[    15.976] (II) fglrx(0): redX: 0.646 redY: 0.333   greenX: 0.315 greenY: 0.620
[    15.976] (II) fglrx(0): blueX: 0.151 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[    15.976] (II) fglrx(0): Supported established timings:
[    15.976] (II) fglrx(0): 720x400@70Hz
[    15.976] (II) fglrx(0): 640x480@60Hz
[    15.976] (II) fglrx(0): 640x480@67Hz
[    15.976] (II) fglrx(0): 640x480@72Hz
[    15.976] (II) fglrx(0): 640x480@75Hz
[    15.976] (II) fglrx(0): 800x600@56Hz
[    15.976] (II) fglrx(0): 800x600@60Hz
[    15.976] (II) fglrx(0): 800x600@72Hz
[    15.976] (II) fglrx(0): 800x600@75Hz
[    15.976] (II) fglrx(0): 832x624@75Hz
[    15.976] (II) fglrx(0): 1024x768@60Hz
[    15.976] (II) fglrx(0): 1024x768@70Hz
[    15.976] (II) fglrx(0): 1024x768@75Hz
[    15.976] (II) fglrx(0): 1280x1024@75Hz
[    15.976] (II) fglrx(0): 1152x864@75Hz
[    15.976] (II) fglrx(0): Manufacturer's mask: 0
[    15.976] (II) fglrx(0): Supported standard timings:
[    15.976] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.976] (II) fglrx(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.976] (II) fglrx(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.976] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.976] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.976] (II) fglrx(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    15.976] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.976] (II) fglrx(0): Supported detailed timing:
[    15.976] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    15.976] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.976] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.976] (II) fglrx(0): Supported detailed timing:
[    15.976] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    15.977] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    15.977] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.977] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    15.977] (II) fglrx(0): Monitor name: S24D300
[    15.977] (II) fglrx(0): Supported detailed timing:
[    15.977] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    15.977] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    15.977] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.977] (II) fglrx(0): Supported detailed timing:
[    15.977] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    15.977] (II) fglrx(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    15.977] (II) fglrx(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    15.977] (II) fglrx(0): Supported detailed timing:
[    15.977] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    15.977] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    15.977] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    15.977] (II) fglrx(0): Number of EDID sections to follow: 1
[    15.977] (II) fglrx(0): EDID (in hex):
[    15.977] (II) fglrx(0): 	00ffffffffffff004c2d430b38353330
[    15.977] (II) fglrx(0): 	1818010380351e782a9ff5a555509e26
[    15.977] (II) fglrx(0): 	105054bfef80714f81c0810081809500
[    15.977] (II) fglrx(0): 	a9c0b3000101023a801871382d40582c
[    15.977] (II) fglrx(0): 	4500132b2100001e011d007251d01e20
[    15.977] (II) fglrx(0): 	6e285500132b2100001e000000fd0032
[    15.977] (II) fglrx(0): 	4b1e5111000a202020202020000000fc
[    15.977] (II) fglrx(0): 	00533234443330300a2020202020018a
[    15.977] (II) fglrx(0): User Preference Output DFP5 using refresh rate 60.0 Hz.
[    15.977] (II) fglrx(0): Printing probed modes for output DFP5
[    15.977] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz UeP)
[    15.977] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    15.977] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    15.977] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    15.977] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.977] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.977] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x800"x50.0  148.50  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.977] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1152x864"x59.9  148.35  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    15.977] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    15.977] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.977] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    15.977] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    15.977] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    15.977] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    15.977] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.977] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "720x576"x59.9  148.35  720 2008 2052 2200  576 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    15.977] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.977] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    15.977] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[    15.977] (II) fglrx(0): Modeline "640x480"x67.0   26.75  640 656 720 800  480 483 487 502 -hsync +vsync (33.4 kHz e)
[    15.977] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.977] (II) fglrx(0): EDID for output DFP6
[    15.977] (II) fglrx(0): EDID for output DFP7
[    15.977] (II) fglrx(0): EDID for output CRT1
[    15.977] (II) fglrx(0): Output DFP1 disconnected
[    15.977] (II) fglrx(0): Output DFP2 disconnected
[    15.977] (II) fglrx(0): Output DFP3 disconnected
[    15.977] (II) fglrx(0): Output DFP4 disconnected
[    15.977] (II) fglrx(0): Output DFP5 connected
[    15.978] (II) fglrx(0): Output DFP6 disconnected
[    15.978] (II) fglrx(0): Output DFP7 disconnected
[    15.978] (II) fglrx(0): Output CRT1 disconnected
[    15.978] (II) fglrx(0): Using user preference for initial modes
[    15.978] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    15.978] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.978] (II) fglrx(0): DPI set to (96, 96)
[    15.978] (II) fglrx(0): Eyefinity capable adapter detected.
[    15.978] (II) fglrx(0): Adapter AMD Radeon HD 6900 Series  has 6 configurable heads and 1 displays connected.
[    15.978] (==) fglrx(0):  PseudoColor visuals disabled
[    15.978] (II) Loading sub module "ramdac"
[    15.978] (II) LoadModule: "ramdac"
[    15.978] (II) Module "ramdac" already built-in
[    15.978] (==) fglrx(0): NoDRI = NO
[    15.978] (==) fglrx(0): Capabilities: 0x00000000
[    15.978] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    15.978] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    15.978] (==) fglrx(0): UseFastTLS=0
[    15.978] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    15.978] (II) fglrx(1): === [xdl_xs115_atiddxPreInit] === begin
[    15.978] (II) Loading sub module "vgahw"
[    15.978] (II) LoadModule: "vgahw"
[    15.978] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    15.978] (II) Module vgahw: vendor="X.Org Foundation"
[    15.978] 	compiled for 1.15.1, module version = 0.1.0
[    15.978] 	ABI class: X.Org Video Driver, version 15.0
[    15.979] (**) fglrx(1): Depth 24, (--) framebuffer bpp 32
[    15.979] (II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.979] (==) fglrx(1): Default visual is TrueColor
[    15.979] (**) fglrx(1): Option "Monitor-Default Monitor" "1-Default monitor"
[    15.979] (==) fglrx(1): RGB weight 888
[    15.979] (II) fglrx(1): Using 8 bits per RGB 
[    15.979] (==) fglrx(1): Buffer Tiling is ON
[    15.979] (II) Loading sub module "fglrxdrm"
[    15.979] (II) LoadModule: "fglrxdrm"
[    15.979] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    15.979] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    15.979] 	compiled for 1.4.99.906, module version = 13.35.5
[    15.993] ukiDynamicMajor: found major device number 250
[    15.993] ukiDynamicMajor: found major device number 250
[    15.993] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.993] ukiOpenDevice: node name is /dev/ati/card0
[    15.993] ukiOpenDevice: open result is 12, (OK)
[    15.993] ukiOpenByBusid: ukiOpenMinor returns 12
[    15.993] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.993] (WW) fglrx(1): Unable to register ADL handler for 0x00C00000
[    15.993] (**) fglrx(1): NoAccel = NO
[    15.993] (**) fglrx(1): AMD 2D Acceleration Architecture enabled
[    15.993] (--) fglrx(1): Chipset: "AMD Radeon HD 6450" (Chipset = 0x6779)
[    15.993] (--) fglrx(1): (PciSubVendor = 0x174b, PciSubDevice = 0xe206)
[    15.993] (==) fglrx(1): board vendor info: third party graphics adapter - NOT original AMD
[    15.993] (--) fglrx(1): Linear framebuffer (phys) at 0xc0000000
[    15.993] (--) fglrx(1): MMIO registers at 0xfdcc0000
[    15.993] (--) fglrx(1): I/O port at 0x0000ce00
[    15.993] (==) fglrx(1): ROM-BIOS at 0x000c0000
[    15.993] (II) fglrx(0): AC Adapter is used
[    15.996] (II) fglrx(1): Primary V_BIOS segment is: 0xc000
[    15.997] (II) Loading sub module "vbe"
[    15.997] (II) LoadModule: "vbe"
[    15.997] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    15.997] (II) Module vbe: vendor="X.Org Foundation"
[    15.997] 	compiled for 1.15.1, module version = 1.1.0
[    15.997] 	ABI class: X.Org Video Driver, version 15.0
[    15.998] (II) fglrx(1): VESA BIOS detected
[    15.998] (II) fglrx(1): VESA VBE Version 3.0
[    15.998] (II) fglrx(1): VESA VBE Total Mem: 16384 kB
[    15.998] (II) fglrx(1): VESA VBE OEM: AMD ATOMBIOS
[    15.998] (II) fglrx(1): VESA VBE OEM Software Rev: 13.12
[    15.998] (II) fglrx(1): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    15.998] (II) fglrx(1): VESA VBE OEM Product: -SH6
[    15.998] (II) fglrx(1): VESA VBE OEM Product Rev: 01.00
[    15.998] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    15.998] (--) fglrx(1): Video RAM: 1048576 kByte, Type: DDR3
[    15.998] (II) fglrx(1): PCIE card detected
[    15.998] (--) fglrx(1): Using per-process page tables (PPPT) as GART.
[    15.998] (WW) fglrx(1): board is an unknown third party board, chipset is supported
[    15.998] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    15.998] (II) fglrx(1): RandR 1.2 support is enabled!
[    15.998] (II) fglrx(1): RandR 1.2 rotation support is enabled!
[    15.998] (II) Loading sub module "fb"
[    15.998] (II) LoadModule: "fb"
[    15.998] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.998] (II) Module fb: vendor="X.Org Foundation"
[    15.998] 	compiled for 1.15.1, module version = 1.0.0
[    15.998] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.998] (II) fglrx(0): EDID Management option: EDID Management is enabled
[    15.998] (II) Loading sub module "ddc"
[    15.998] (II) LoadModule: "ddc"
[    15.998] (II) Module "ddc" already built-in
[    16.118] (II) fglrx(1): Output DFP1 has no monitor section
[    16.118] (II) fglrx(1): Output DFP2 has no monitor section
[    16.118] (II) fglrx(1): Output DFP3 has no monitor section
[    16.118] (II) fglrx(1): Output CRT1 has no monitor section
[    16.118] (II) Loading sub module "ddc"
[    16.118] (II) LoadModule: "ddc"
[    16.118] (II) Module "ddc" already built-in
[    16.118] (II) fglrx(1): Connected Display0: DFP1
[    16.118] (II) fglrx(1): Display0 EDID data ---------------------------
[    16.118] (II) fglrx(1): Manufacturer: SAM  Model: b43  Serial#: 808662328
[    16.118] (II) fglrx(1): Year: 2014  Week: 25
[    16.118] (II) fglrx(1): EDID Version: 1.3
[    16.118] (II) fglrx(1): Digital Display Input
[    16.118] (II) fglrx(1): Max Image Size [cm]: horiz.: 53  vert.: 30
[    16.118] (II) fglrx(1): Gamma: 2.20
[    16.118] (II) fglrx(1): DPMS capabilities: Off
[    16.118] (II) fglrx(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.118] (II) fglrx(1): First detailed timing is preferred mode
[    16.118] (II) fglrx(1): redX: 0.646 redY: 0.333   greenX: 0.315 greenY: 0.620
[    16.118] (II) fglrx(1): blueX: 0.151 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[    16.118] (II) fglrx(1): Supported established timings:
[    16.118] (II) fglrx(1): 720x400@70Hz
[    16.118] (II) fglrx(1): 640x480@60Hz
[    16.118] (II) fglrx(1): 640x480@67Hz
[    16.118] (II) fglrx(1): 640x480@72Hz
[    16.118] (II) fglrx(1): 640x480@75Hz
[    16.118] (II) fglrx(1): 800x600@56Hz
[    16.118] (II) fglrx(1): 800x600@60Hz
[    16.118] (II) fglrx(1): 800x600@72Hz
[    16.118] (II) fglrx(1): 800x600@75Hz
[    16.118] (II) fglrx(1): 832x624@75Hz
[    16.118] (II) fglrx(1): 1024x768@60Hz
[    16.118] (II) fglrx(1): 1024x768@70Hz
[    16.118] (II) fglrx(1): 1024x768@75Hz
[    16.118] (II) fglrx(1): 1280x1024@75Hz
[    16.118] (II) fglrx(1): 1152x864@75Hz
[    16.118] (II) fglrx(1): Manufacturer's mask: 0
[    16.118] (II) fglrx(1): Supported standard timings:
[    16.118] (II) fglrx(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.118] (II) fglrx(1): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    16.118] (II) fglrx(1): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    16.118] (II) fglrx(1): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.118] (II) fglrx(1): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    16.119] (II) fglrx(1): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    16.119] (II) fglrx(1): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    16.119] (II) fglrx(1): Supported detailed timing:
[    16.119] (II) fglrx(1): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    16.119] (II) fglrx(1): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    16.119] (II) fglrx(1): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    16.119] (II) fglrx(1): Supported detailed timing:
[    16.119] (II) fglrx(1): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    16.119] (II) fglrx(1): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    16.119] (II) fglrx(1): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    16.119] (II) fglrx(1): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    16.119] (II) fglrx(1): Monitor name: S24D300
[    16.119] (II) fglrx(1): Supported detailed timing:
[    16.119] (II) fglrx(1): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    16.119] (II) fglrx(1): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    16.119] (II) fglrx(1): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    16.119] (II) fglrx(1): Supported detailed timing:
[    16.119] (II) fglrx(1): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    16.119] (II) fglrx(1): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    16.119] (II) fglrx(1): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    16.119] (II) fglrx(1): Supported detailed timing:
[    16.119] (II) fglrx(1): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    16.119] (II) fglrx(1): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    16.119] (II) fglrx(1): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    16.119] (II) fglrx(1): Number of EDID sections to follow: 1
[    16.119] (II) fglrx(1): EDID (in hex):
[    16.119] (II) fglrx(1): 	00ffffffffffff004c2d430b38353330
[    16.119] (II) fglrx(1): 	1918010380351e782a9ff5a555509e26
[    16.119] (II) fglrx(1): 	105054bfef80714f81c0810081809500
[    16.119] (II) fglrx(1): 	a9c0b3000101023a801871382d40582c
[    16.119] (II) fglrx(1): 	4500132b2100001e011d007251d01e20
[    16.119] (II) fglrx(1): 	6e285500132b2100001e000000fd0032
[    16.119] (II) fglrx(1): 	4b1e5111000a202020202020000000fc
[    16.119] (II) fglrx(1): 	00533234443330300a20202020200189
[    16.119] (II) fglrx(1): End of Display0 EDID data --------------------
[    16.119] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    16.120] (II) fglrx(1): EDID for output DFP1
[    16.120] (II) fglrx(1): Manufacturer: SAM  Model: b43  Serial#: 808662328
[    16.120] (II) fglrx(1): Year: 2014  Week: 25
[    16.120] (II) fglrx(1): EDID Version: 1.3
[    16.120] (II) fglrx(1): Digital Display Input
[    16.120] (II) fglrx(1): Max Image Size [cm]: horiz.: 53  vert.: 30
[    16.120] (II) fglrx(1): Gamma: 2.20
[    16.120] (II) fglrx(1): DPMS capabilities: Off
[    16.120] (II) fglrx(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.120] (II) fglrx(1): First detailed timing is preferred mode
[    16.120] (II) fglrx(1): redX: 0.646 redY: 0.333   greenX: 0.315 greenY: 0.620
[    16.120] (II) fglrx(1): blueX: 0.151 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
[    16.120] (II) fglrx(1): Supported established timings:
[    16.120] (II) fglrx(1): 720x400@70Hz
[    16.120] (II) fglrx(1): 640x480@60Hz
[    16.120] (II) fglrx(1): 640x480@67Hz
[    16.120] (II) fglrx(1): 640x480@72Hz
[    16.120] (II) fglrx(1): 640x480@75Hz
[    16.120] (II) fglrx(1): 800x600@56Hz
[    16.120] (II) fglrx(1): 800x600@60Hz
[    16.120] (II) fglrx(1): 800x600@72Hz
[    16.120] (II) fglrx(1): 800x600@75Hz
[    16.120] (II) fglrx(1): 832x624@75Hz
[    16.120] (II) fglrx(1): 1024x768@60Hz
[    16.120] (II) fglrx(1): 1024x768@70Hz
[    16.120] (II) fglrx(1): 1024x768@75Hz
[    16.120] (II) fglrx(1): 1280x1024@75Hz
[    16.120] (II) fglrx(1): 1152x864@75Hz
[    16.120] (II) fglrx(1): Manufacturer's mask: 0
[    16.120] (II) fglrx(1): Supported standard timings:
[    16.120] (II) fglrx(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.120] (II) fglrx(1): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    16.120] (II) fglrx(1): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    16.120] (II) fglrx(1): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.120] (II) fglrx(1): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    16.120] (II) fglrx(1): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    16.120] (II) fglrx(1): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    16.120] (II) fglrx(1): Supported detailed timing:
[    16.120] (II) fglrx(1): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    16.120] (II) fglrx(1): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    16.120] (II) fglrx(1): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    16.120] (II) fglrx(1): Supported detailed timing:
[    16.120] (II) fglrx(1): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    16.120] (II) fglrx(1): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    16.120] (II) fglrx(1): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    16.120] (II) fglrx(1): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    16.120] (II) fglrx(1): Monitor name: S24D300
[    16.120] (II) fglrx(1): Supported detailed timing:
[    16.120] (II) fglrx(1): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    16.120] (II) fglrx(1): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    16.120] (II) fglrx(1): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    16.120] (II) fglrx(1): Supported detailed timing:
[    16.120] (II) fglrx(1): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    16.120] (II) fglrx(1): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    16.120] (II) fglrx(1): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    16.120] (II) fglrx(1): Supported detailed timing:
[    16.120] (II) fglrx(1): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    16.120] (II) fglrx(1): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    16.120] (II) fglrx(1): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    16.120] (II) fglrx(1): Number of EDID sections to follow: 1
[    16.120] (II) fglrx(1): EDID (in hex):
[    16.120] (II) fglrx(1): 	00ffffffffffff004c2d430b38353330
[    16.120] (II) fglrx(1): 	1918010380351e782a9ff5a555509e26
[    16.120] (II) fglrx(1): 	105054bfef80714f81c0810081809500
[    16.120] (II) fglrx(1): 	a9c0b3000101023a801871382d40582c
[    16.120] (II) fglrx(1): 	4500132b2100001e011d007251d01e20
[    16.120] (II) fglrx(1): 	6e285500132b2100001e000000fd0032
[    16.120] (II) fglrx(1): 	4b1e5111000a202020202020000000fc
[    16.120] (II) fglrx(1): 	00533234443330300a20202020200189
[    16.120] (II) fglrx(1): EDID vendor "SAM", prod id 2883
[    16.124] (II) fglrx(1): Using EDID range info for horizontal sync
[    16.124] (II) fglrx(1): Using EDID range info for vertical refresh
[    16.124] (II) fglrx(1): Printing DDC gathered Modelines:
[    16.124] (II) fglrx(1): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    16.124] (II) fglrx(1): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.124] (II) fglrx(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.124] (II) fglrx(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.124] (II) fglrx(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.124] (II) fglrx(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.124] (II) fglrx(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.124] (II) fglrx(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    16.124] (II) fglrx(1): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    16.124] (II) fglrx(1): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    16.124] (II) fglrx(1): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    16.124] (II) fglrx(1): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    16.124] (II) fglrx(1): Printing probed modes for output DFP1
[    16.124] (II) fglrx(1): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    16.124] (II) fglrx(1): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    16.124] (II) fglrx(1): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    16.124] (II) fglrx(1): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    16.124] (II) fglrx(1): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    16.124] (II) fglrx(1): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    16.124] (II) fglrx(1): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.124] (II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x800"x50.0  148.50  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    16.125] (II) fglrx(1): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1152x864"x59.9  148.35  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    16.125] (II) fglrx(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.125] (II) fglrx(1): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.125] (II) fglrx(1): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    16.125] (II) fglrx(1): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    16.125] (II) fglrx(1): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.125] (II) fglrx(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.125] (II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.125] (II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "720x576"x59.9  148.35  720 2008 2052 2200  576 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    16.125] (II) fglrx(1): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    16.125] (II) fglrx(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.125] (II) fglrx(1): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[    16.125] (II) fglrx(1): Modeline "640x480"x67.0   26.75  640 656 720 800  480 483 487 502 -hsync +vsync (33.4 kHz e)
[    16.125] (II) fglrx(1): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.125] (II) fglrx(1): EDID for output DFP2
[    16.125] (II) fglrx(1): EDID for output DFP3
[    16.125] (II) fglrx(1): EDID for output CRT1
[    16.125] (II) fglrx(1): Output DFP1 connected
[    16.125] (II) fglrx(1): Output DFP2 disconnected
[    16.125] (II) fglrx(1): Output DFP3 disconnected
[    16.125] (II) fglrx(1): Output CRT1 disconnected
[    16.125] (II) fglrx(1): Using exact sizes for initial modes
[    16.125] (II) fglrx(1): Output DFP1 using initial mode 1920x1080
[    16.125] (II) fglrx(1): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.125] (II) fglrx(1): Display dimensions: (530, 300) mm
[    16.125] (II) fglrx(1): DPI set to (92, 92)
[    16.125] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    16.125] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    16.125] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    16.125] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    16.125] (II) fglrx(1): Eyefinity capable adapter detected.
[    16.125] (II) fglrx(1): Adapter AMD Radeon HD 6450 has 3 configurable heads and 1 displays connected.
[    16.125] (==) fglrx(1):  PseudoColor visuals disabled
[    16.125] (II) Loading sub module "ramdac"
[    16.125] (II) LoadModule: "ramdac"
[    16.125] (II) Module "ramdac" already built-in
[    16.125] (==) fglrx(1): NoDRI = NO
[    16.125] (==) fglrx(1): Capabilities: 0x00000000
[    16.125] (==) fglrx(1): CapabilitiesEx: 0x00000000
[    16.125] (==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
[    16.125] (==) fglrx(1): UseFastTLS=0
[    16.125] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    16.125] (--) Depth 24 pixmap format is 32 bpp
[    16.125] Loading extension ATIFGLRXDRI
[    16.125] (II) fglrx(0): doing swlDriScreenInit
[    16.126] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    16.126] ukiDynamicMajor: found major device number 250
[    16.126] ukiDynamicMajor: found major device number 250
[    16.126] ukiDynamicMajor: found major device number 250
[    16.126] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    16.126] ukiOpenDevice: node name is /dev/ati/card0
[    16.126] ukiOpenDevice: open result is 13, (OK)
[    16.126] ukiOpenByBusid: ukiOpenMinor returns 13
[    16.126] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.126] ukiOpenDevice: node name is /dev/ati/card1
[    16.126] ukiOpenDevice: open result is 13, (OK)
[    16.126] ukiOpenByBusid: ukiOpenMinor returns 13
[    16.126] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.126] (II) fglrx(0): [uki] DRM interface version 1.0
[    16.126] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    16.126] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    16.126] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f0bebe46000
[    16.126] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    16.126] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    16.126] (II) fglrx(0): swlDriScreenInit done
[    16.126] (II) fglrx(0): Kernel Module Version Information:
[    16.126] (II) fglrx(0):     Name: fglrx
[    16.126] (II) fglrx(0):     Version: 13.35.5
[    16.126] (II) fglrx(0):     Date: Mar 12 2014
[    16.126] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    16.126] (II) fglrx(0): Kernel Module version matches driver.
[    16.126] (II) fglrx(0): Kernel Module Build Time Information:
[    16.126] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-37-generic
[    16.126] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    16.126] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    16.126] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    16.126] (II) fglrx(0): [uki] register handle = 0x00004000
[    16.126] (II) fglrx(0): DRI initialization successfull
[    16.126] (II) fglrx(0): FBADPhys: 0xf800000000 FBMappedSize: 0x010e0000
[    16.127] (==) fglrx(0): Backing store enabled
[    16.127] Loading extension FGLRXEXTENSION
[    16.127] (==) fglrx(0): DPMS enabled
[    16.127] (II) fglrx(0): Initialized in-driver Xinerama extension
[    16.127] (**) fglrx(0): Textured Video is enabled.
[    16.127] (II) LoadModule: "glesx"
[    16.127] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    16.128] (II) Module glesx: vendor="X.Org Foundation"
[    16.128] 	compiled for 1.4.99.906, module version = 1.0.0
[    16.128] Loading extension GLESX
[    16.128] (II) fglrx(0): GLESX enableFlags = 8784
[    16.128] (II) fglrx(0): GLESX is enabled
[    16.128] (II) LoadModule: "amdxmm"
[    16.128] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    16.128] (II) Module amdxmm: vendor="X.Org Foundation"
[    16.128] 	compiled for 1.4.99.906, module version = 2.0.0
[    16.160] Loading extension AMDXVOPL
[    16.160] Loading extension AMDXVBA
[    16.161] (II) fglrx(0): Composite extension is not loaded
[    16.161] (II) fglrx(0): X context handle = 0x1
[    16.161] (II) fglrx(0): [DRI] installation complete
[    16.161] (==) fglrx(0): Silken mouse enabled
[    16.161] (==) fglrx(0): Using HW cursor of display infrastructure!
[    16.161] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.196] (--) RandR disabled
[    16.196] (II) fglrx(1): doing swlDriScreenInit
[    16.196] (II) fglrx(1): swlDriScreenInit for fglrx driver
[    16.196] ukiDynamicMajor: found major device number 250
[    16.196] ukiDynamicMajor: found major device number 250
[    16.196] ukiDynamicMajor: found major device number 250
[    16.196] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.196] ukiOpenDevice: node name is /dev/ati/card0
[    16.196] ukiOpenDevice: open result is 14, (OK)
[    16.196] ukiOpenByBusid: ukiOpenMinor returns 14
[    16.196] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.196] (II) fglrx(1): [uki] DRM interface version 1.0
[    16.196] (II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    16.196] (II) fglrx(1): [uki] added 8192 byte SAREA at 0x18000
[    16.196] (II) fglrx(1): [uki] mapped SAREA 0x18000 to 0x7f0be46e4000
[    16.196] (II) fglrx(1): [uki] framebuffer handle = 0x19000
[    16.196] (II) fglrx(1): [uki] added 1 reserved context for kernel
[    16.196] (II) fglrx(1): swlDriScreenInit done
[    16.196] (II) fglrx(1): Kernel Module Version Information:
[    16.196] (II) fglrx(1):     Name: fglrx
[    16.196] (II) fglrx(1):     Version: 13.35.5
[    16.196] (II) fglrx(1):     Date: Mar 12 2014
[    16.196] (II) fglrx(1):     Desc: AMD FireGL DRM kernel module
[    16.196] (II) fglrx(1): Kernel Module version matches driver.
[    16.196] (II) fglrx(1): Kernel Module Build Time Information:
[    16.196] (II) fglrx(1):     Build-Kernel UTS_RELEASE:        3.13.0-37-generic
[    16.196] (II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
[    16.196] (II) fglrx(1):     Build-Kernel __SMP__:            yes
[    16.196] (II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
[    16.196] (II) fglrx(1): [uki] register handle = 0x0001a000
[    16.197] (II) fglrx(1): DRI initialization successfull
[    16.197] (II) fglrx(1): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    16.197] (==) fglrx(1): Backing store disabled
[    16.197] (==) fglrx(1): DPMS enabled
[    16.197] (**) fglrx(1): Textured Video is enabled.
[    16.197] (II) fglrx(1): GLESX enableFlags = 8784
[    16.197] (II) fglrx(1): GLESX is enabled
[    16.223] Loading extension AMDXVOPL
[    16.223] Loading extension AMDXVBA
[    16.224] (II) fglrx(1): Composite extension is not loaded
[    16.224] (II) fglrx(1): X context handle = 0x1
[    16.224] (II) fglrx(1): [DRI] installation complete
[    16.224] (==) fglrx(1): Silken mouse enabled
[    16.224] (==) fglrx(1): Using HW cursor of display infrastructure!
[    16.224] (II) fglrx(1): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.279] (--) RandR disabled
[    16.283] (II) SELinux: Disabled on system
[    16.283] ukiDynamicMajor: found major device number 250
[    16.283] ukiDynamicMajor: found major device number 250
[    16.284] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    16.284] ukiOpenDevice: node name is /dev/ati/card0
[    16.284] ukiOpenDevice: open result is 15, (OK)
[    16.284] ukiOpenByBusid: ukiOpenMinor returns 15
[    16.284] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.284] ukiOpenDevice: node name is /dev/ati/card1
[    16.284] ukiOpenDevice: open result is 15, (OK)
[    16.284] ukiOpenByBusid: ukiOpenMinor returns 15
[    16.284] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.284] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    16.284] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    16.284] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    16.320] ukiDynamicMajor: found major device number 250
[    16.320] ukiDynamicMajor: found major device number 250
[    16.320] ukiDynamicMajor: found major device number 250
[    16.320] ukiOpenDevice: node name is /dev/ati/card0
[    16.320] ukiOpenDevice: open result is 16, (OK)
[    16.320] ukiGetBusid returned 'PCI:1:0:0'
[    16.320] ukiOpenDevice: node name is /dev/ati/card1
[    16.321] ukiOpenDevice: open result is 16, (OK)
[    16.321] ukiGetBusid returned 'PCI:2:0:0'
[    16.321] ukiOpenDevice: node name is /dev/ati/card2
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card3
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card4
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card5
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card6
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card7
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card8
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card9
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card10
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card11
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card12
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card13
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card14
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiOpenDevice: node name is /dev/ati/card15
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: open result is -1, (No such device)
[    16.321] ukiOpenDevice: Open failed
[    16.321] ukiDynamicMajor: found major device number 250
[    16.321] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.321] ukiOpenDevice: node name is /dev/ati/card0
[    16.321] ukiOpenDevice: open result is 16, (OK)
[    16.321] ukiOpenByBusid: ukiOpenMinor returns 16
[    16.321] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.437] ukiDynamicMajor: found major device number 250
[    16.437] ukiDynamicMajor: found major device number 250
[    16.437] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.437] ukiOpenDevice: node name is /dev/ati/card0
[    16.437] ukiOpenDevice: open result is 17, (OK)
[    16.437] ukiOpenByBusid: ukiOpenMinor returns 17
[    16.437] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.456] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    16.456] ukiDynamicMajor: found major device number 250
[    16.456] ukiDynamicMajor: found major device number 250
[    16.456] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.456] ukiOpenDevice: node name is /dev/ati/card0
[    16.456] ukiOpenDevice: open result is 18, (OK)
[    16.456] ukiOpenByBusid: ukiOpenMinor returns 18
[    16.456] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.456] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 1
[    16.457] ukiDynamicMajor: found major device number 250
[    16.457] ukiDynamicMajor: found major device number 250
[    16.457] ukiDynamicMajor: found major device number 250
[    16.457] ukiOpenDevice: node name is /dev/ati/card0
[    16.457] ukiOpenDevice: open result is 19, (OK)
[    16.457] ukiGetBusid returned 'PCI:1:0:0'
[    16.457] ukiOpenDevice: node name is /dev/ati/card1
[    16.457] ukiOpenDevice: open result is 19, (OK)
[    16.457] ukiGetBusid returned 'PCI:2:0:0'
[    16.457] ukiOpenDevice: node name is /dev/ati/card2
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card3
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card4
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card5
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card6
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card7
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card8
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card9
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card10
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: Open failed
[    16.457] ukiOpenDevice: node name is /dev/ati/card11
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.457] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: Open failed
[    16.458] ukiOpenDevice: node name is /dev/ati/card12
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: Open failed
[    16.458] ukiOpenDevice: node name is /dev/ati/card13
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: Open failed
[    16.458] ukiOpenDevice: node name is /dev/ati/card14
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: Open failed
[    16.458] ukiOpenDevice: node name is /dev/ati/card15
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: open result is -1, (No such device)
[    16.458] ukiOpenDevice: Open failed
[    16.458] ukiDynamicMajor: found major device number 250
[    16.458] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.458] ukiOpenDevice: node name is /dev/ati/card0
[    16.458] ukiOpenDevice: open result is 19, (OK)
[    16.458] ukiOpenByBusid: ukiOpenMinor returns 19
[    16.458] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.474] (II) fglrx(0): OverDrive5 Detected!
[    16.479] (II) fglrx(0): OverDrive5 Detected!
[    16.491] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.494] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.494] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.494] (II) LoadModule: "evdev"
[    16.494] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.495] (II) Module evdev: vendor="X.Org Foundation"
[    16.495] 	compiled for 1.15.0, module version = 2.8.2
[    16.495] 	Module class: X.Org XInput Driver
[    16.495] 	ABI class: X.Org XInput driver, version 20.0
[    16.495] (II) Using input driver 'evdev' for 'Power Button'
[    16.495] (**) Power Button: always reports core events
[    16.495] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.495] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.495] (--) evdev: Power Button: Found keys
[    16.495] (II) evdev: Power Button: Configuring as keyboard
[    16.495] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.495] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.495] (**) Option "xkb_rules" "evdev"
[    16.495] (**) Option "xkb_model" "pc105"
[    16.495] (**) Option "xkb_layout" "us"
[    16.496] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.496] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.496] (II) Using input driver 'evdev' for 'Power Button'
[    16.496] (**) Power Button: always reports core events
[    16.496] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.496] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.496] (--) evdev: Power Button: Found keys
[    16.496] (II) evdev: Power Button: Configuring as keyboard
[    16.496] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.496] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    16.496] (**) Option "xkb_rules" "evdev"
[    16.496] (**) Option "xkb_model" "pc105"
[    16.496] (**) Option "xkb_layout" "us"
[    16.496] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event14)
[    16.496] (II) No input driver specified, ignoring this device.
[    16.496] (II) This device may have been added with another device file.
[    16.497] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event15)
[    16.497] (II) No input driver specified, ignoring this device.
[    16.497] (II) This device may have been added with another device file.
[    16.497] (II) config/udev: Adding input device SONiX SI Gaming Keyboard (/dev/input/event4)
[    16.497] (**) SONiX SI Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.497] (II) Using input driver 'evdev' for 'SONiX SI Gaming Keyboard'
[    16.497] (**) SONiX SI Gaming Keyboard: always reports core events
[    16.497] (**) evdev: SONiX SI Gaming Keyboard: Device: "/dev/input/event4"
[    16.497] (--) evdev: SONiX SI Gaming Keyboard: Vendor 0xc45 Product 0x8603
[    16.497] (--) evdev: SONiX SI Gaming Keyboard: Found keys
[    16.497] (II) evdev: SONiX SI Gaming Keyboard: Configuring as keyboard
[    16.497] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input5/event4"
[    16.497] (II) XINPUT: Adding extended input device "SONiX SI Gaming Keyboard" (type: KEYBOARD, id 8)
[    16.497] (**) Option "xkb_rules" "evdev"
[    16.497] (**) Option "xkb_model" "pc105"
[    16.497] (**) Option "xkb_layout" "us"
[    16.497] (II) config/udev: Adding input device SONiX SI Gaming Keyboard (/dev/input/event5)
[    16.497] (**) SONiX SI Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.497] (II) Using input driver 'evdev' for 'SONiX SI Gaming Keyboard'
[    16.497] (**) SONiX SI Gaming Keyboard: always reports core events
[    16.497] (**) evdev: SONiX SI Gaming Keyboard: Device: "/dev/input/event5"
[    16.497] (--) evdev: SONiX SI Gaming Keyboard: Vendor 0xc45 Product 0x8603
[    16.497] (--) evdev: SONiX SI Gaming Keyboard: Found 1 mouse buttons
[    16.497] (--) evdev: SONiX SI Gaming Keyboard: Found scroll wheel(s)
[    16.498] (--) evdev: SONiX SI Gaming Keyboard: Found relative axes
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: Forcing relative x/y axes to exist.
[    16.498] (--) evdev: SONiX SI Gaming Keyboard: Found absolute axes
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: Forcing absolute x/y axes to exist.
[    16.498] (--) evdev: SONiX SI Gaming Keyboard: Found keys
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: Configuring as mouse
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: Configuring as keyboard
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: Adding scrollwheel support
[    16.498] (**) evdev: SONiX SI Gaming Keyboard: YAxisMapping: buttons 4 and 5
[    16.498] (**) evdev: SONiX SI Gaming Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.498] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input6/event5"
[    16.498] (II) XINPUT: Adding extended input device "SONiX SI Gaming Keyboard" (type: KEYBOARD, id 9)
[    16.498] (**) Option "xkb_rules" "evdev"
[    16.498] (**) Option "xkb_model" "pc105"
[    16.498] (**) Option "xkb_layout" "us"
[    16.498] (II) evdev: SONiX SI Gaming Keyboard: initialized for relative axes.
[    16.498] (WW) evdev: SONiX SI Gaming Keyboard: ignoring absolute axes.
[    16.498] (**) SONiX SI Gaming Keyboard: (accel) keeping acceleration scheme 1
[    16.498] (**) SONiX SI Gaming Keyboard: (accel) acceleration profile 0
[    16.498] (**) SONiX SI Gaming Keyboard: (accel) acceleration factor: 2.000
[    16.498] (**) SONiX SI Gaming Keyboard: (accel) acceleration threshold: 4
[    16.498] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/event2)
[    16.498] (**) Holtek USB Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[    16.498] (II) Using input driver 'evdev' for 'Holtek USB Gaming Mouse'
[    16.498] (**) Holtek USB Gaming Mouse: always reports core events
[    16.498] (**) evdev: Holtek USB Gaming Mouse: Device: "/dev/input/event2"
[    16.498] (--) evdev: Holtek USB Gaming Mouse: Vendor 0x4d9 Product 0xa070
[    16.498] (--) evdev: Holtek USB Gaming Mouse: Found keys
[    16.498] (II) evdev: Holtek USB Gaming Mouse: Configuring as keyboard
[    16.498] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input3/event2"
[    16.498] (II) XINPUT: Adding extended input device "Holtek USB Gaming Mouse" (type: KEYBOARD, id 10)
[    16.498] (**) Option "xkb_rules" "evdev"
[    16.498] (**) Option "xkb_model" "pc105"
[    16.498] (**) Option "xkb_layout" "us"
[    16.499] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/event3)
[    16.499] (**) Holtek USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[    16.499] (**) Holtek USB Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[    16.499] (II) Using input driver 'evdev' for 'Holtek USB Gaming Mouse'
[    16.499] (**) Holtek USB Gaming Mouse: always reports core events
[    16.499] (**) evdev: Holtek USB Gaming Mouse: Device: "/dev/input/event3"
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Vendor 0x4d9 Product 0xa070
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found 9 mouse buttons
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found scroll wheel(s)
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found relative axes
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found x and y relative axes
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found absolute axes
[    16.499] (II) evdev: Holtek USB Gaming Mouse: Forcing absolute x/y axes to exist.
[    16.499] (--) evdev: Holtek USB Gaming Mouse: Found keys
[    16.499] (II) evdev: Holtek USB Gaming Mouse: Configuring as mouse
[    16.499] (II) evdev: Holtek USB Gaming Mouse: Configuring as keyboard
[    16.499] (II) evdev: Holtek USB Gaming Mouse: Adding scrollwheel support
[    16.499] (**) evdev: Holtek USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[    16.499] (**) evdev: Holtek USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.499] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input4/event3"
[    16.499] (II) XINPUT: Adding extended input device "Holtek USB Gaming Mouse" (type: KEYBOARD, id 11)
[    16.499] (**) Option "xkb_rules" "evdev"
[    16.499] (**) Option "xkb_model" "pc105"
[    16.499] (**) Option "xkb_layout" "us"
[    16.499] (II) evdev: Holtek USB Gaming Mouse: initialized for relative axes.
[    16.499] (WW) evdev: Holtek USB Gaming Mouse: ignoring absolute axes.
[    16.500] (**) Holtek USB Gaming Mouse: (accel) keeping acceleration scheme 1
[    16.500] (**) Holtek USB Gaming Mouse: (accel) acceleration profile 0
[    16.500] (**) Holtek USB Gaming Mouse: (accel) acceleration factor: 2.000
[    16.500] (**) Holtek USB Gaming Mouse: (accel) acceleration threshold: 4
[    16.500] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/mouse0)
[    16.500] (II) No input driver specified, ignoring this device.
[    16.500] (II) This device may have been added with another device file.
[    16.500] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event10)
[    16.500] (II) No input driver specified, ignoring this device.
[    16.500] (II) This device may have been added with another device file.
[    16.500] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event9)
[    16.500] (II) No input driver specified, ignoring this device.
[    16.500] (II) This device may have been added with another device file.
[    16.500] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event8)
[    16.500] (II) No input driver specified, ignoring this device.
[    16.500] (II) This device may have been added with another device file.
[    16.501] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event7)
[    16.501] (II) No input driver specified, ignoring this device.
[    16.501] (II) This device may have been added with another device file.
[    16.501] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event6)
[    16.501] (II) No input driver specified, ignoring this device.
[    16.501] (II) This device may have been added with another device file.
[    16.501] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event13)
[    16.501] (II) No input driver specified, ignoring this device.
[    16.501] (II) This device may have been added with another device file.
[    16.501] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event12)
[    16.501] (II) No input driver specified, ignoring this device.
[    16.501] (II) This device may have been added with another device file.
[    16.501] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event11)
[    16.501] (II) No input driver specified, ignoring this device.
[    16.501] (II) This device may have been added with another device file.
[    16.506] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    16.506] (II) fglrx(1): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[   172.184] (II) AIGLX: Suspending AIGLX clients for VT switch
[   172.184] (II) fglrx(0): Backup framebuffer data.
[   172.196] (II) fglrx(0): Backup complete.
[   172.198] (II) AIGLX: Suspending AIGLX clients for VT switch
[   172.198] (II) fglrx(1): Backup framebuffer data.
[   172.199] (II) fglrx(1): Backup complete.



```

---

