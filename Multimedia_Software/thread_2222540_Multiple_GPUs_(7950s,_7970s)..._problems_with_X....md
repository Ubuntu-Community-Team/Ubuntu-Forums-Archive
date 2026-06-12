---
title: "Multiple GPUs (7950s, 7970s)... problems with X?... problems with Catalyst?"
date: 2014-05-07
forum: Multimedia Software
---

### Post by robione on 2014-05-07
I've been beating my head against the wall with this one for a while. (About one week a month for 5 months, LOL) Long story short, I am putting together a mining rig. People have successfully used 6... 7 GPUs with my motherboard. It seems I have problems with multiple cards. It really depends which cards I plug into my mobo but I've had problems with two, with 4, with 5, with 6... I've also had 6 working.... just that the 6th card in  that instance was a 7970 slower than my 7950s (mining) and my PSUs at the time really couldn't handle the load.

I changed my boot to be really verbose. There is no change there. I looked at the Xorg.0.log file and there is a lot of stuff there. A lot of stuff I'd like to remove if I had the know-how (seems like a try something in xorg.conf which consistently results in a hang... specifically relating to display mode selection). But that's kinda extra, right now I would just like help getting X to the desktop.

I've been running 2 XFX DD 7950s on x1->x16 powered risers / air-cooled, 2 HIS 7950s on mobo / watercooled, 1 HIS 7970 on mobo / watercooled. That works. Swapped out the XFX for two more HIS 7950s. Don't work. Today I found one HIS would work, the other would not. Then using the one that would work... I swapped out the remaining XFX 7950 and tested each HIS 7970 I have (2). One is detected by the mobo but hangs, the other is not detected by the mobo.

It has been a frustrating journey. I'm not sure if the log helps shed any light. I'm just posting the one that worked. The one that didn't work made several uki- calls and then seemed to hang waiting for a response. The line with '... 8, (OK)' never appeared, Around the 11.4 second mark. But the card it seemed to be waiting for a response on already successfully responded a couple of times (PCI 3:0:0).

Other system info:
[LIST]
[*]Xubuntu 12.04
[*]Catalyst 13.251
[*]Asrock Z87 UEFI 1.00
[*]CGMiner 3.7.2
[*]X Server 1.11.3
[*]Motherboard: Asrock Z87 Fata1ity Killer
[/LIST]

When determining my X version (literally at cmdline: [$prompt] X -version) it looks like X is compiled for a different linux kernel (2.6.42-37) then my current OS (3.2.0-56). The specific words are "build operating system" and "current operating system."

My long log file:
```
[COLOR=#000000][     9.728] [/COLOR]X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.728] X Protocol Version 11, Revision 0
[     9.728] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     9.728] Current Operating System: Linux canary 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64
[     9.728] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic root=UUID=58f70c44-bb9c-4b45-a865-b08926c0dc73 ro init=/sbin/init -v noplymouth INIT_VERBOSE=yes
[     9.728] Build Date: 11 April 2013  01:05:39PM
[     9.728] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[     9.728] Current version of pixman: 0.24.4
[     9.728]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     9.728] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.728] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May  5 03:47:09 2014
[     9.728] (==) Using config file: "/etc/X11/xorg.conf"
[     9.728] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.728] (==) ServerLayout "aticonfig Layout"
[     9.728] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     9.728] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     9.728] (**) |   |-->Device "aticonfig-Device[0]-0"
[     9.728] (**) |-->Screen "aticonfig-Screen[1]-0" (1)
[     9.728] (**) |   |-->Monitor "aticonfig-Monitor[1]-0"
[     9.728] (**) |   |-->Device "aticonfig-Device[1]-0"
[     9.728] (**) |-->Screen "aticonfig-Screen[2]-0" (2)
[     9.728] (**) |   |-->Monitor "aticonfig-Monitor[2]-0"
[     9.728] (**) |   |-->Device "aticonfig-Device[2]-0"
[     9.728] (**) |-->Screen "aticonfig-Screen[3]-0" (3)
[     9.728] (**) |   |-->Monitor "aticonfig-Monitor[3]-0"
[     9.728] (**) |   |-->Device "aticonfig-Device[3]-0"
[     9.728] (**) |-->Screen "aticonfig-Screen[4]-0" (4)
[     9.728] (**) |   |-->Monitor "aticonfig-Monitor[4]-0"
[     9.728] (**) |   |-->Device "aticonfig-Device[4]-0"
[     9.728] (==) Automatically adding devices
[     9.728] (==) Automatically enabling devices
[     9.867] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.867]     Entry deleted from font path.
[     9.867] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     9.867] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.867] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.867] (II) Loader magic: 0x7f9f9aa76b00
[     9.867] (II) Module ABI versions:
[     9.867]     X.Org ANSI C Emulation: 0.4
[     9.867]     X.Org Video Driver: 11.0
[     9.867]     X.Org XInput driver : 16.0
[     9.867]     X.Org Server Extension : 6.0
[     9.868] (--) PCI:*(0:0:2:0) 8086:0402:1849:0402 rev 6, Mem @ 0xf0400000/4194304, 0x50000000/268435456, I/O @ 0x0000f000/64
[     9.868] (--) PCI: (0:1:0:0) 1002:6798:1787:3000 rev 0, Mem @ 0xe0000000/268435456, 0xf0000000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     9.868] (--) PCI: (0:2:0:0) 1002:679a:1787:201c rev 0, Mem @ 0xc0000000/268435456, 0xd0000000/262144, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[     9.868] (--) PCI: (0:3:0:0) 1002:679a:1787:201c rev 0, Mem @ 0xa0000000/268435456, 0xb0000000/262144, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[     9.868] (--) PCI: (0:5:0:0) 1002:679a:1682:3221 rev 0, Mem @ 0x80000000/268435456, 0x90000000/262144, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[     9.868] (--) PCI: (0:6:0:0) 1002:679a:1682:3221 rev 0, Mem @ 0x60000000/268435456, 0x70000000/262144, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[     9.868] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.868] (II) "extmod" will be loaded by default.
[     9.868] (II) "dbe" will be loaded by default.
[     9.868] (II) "glx" will be loaded by default.
[     9.868] (II) "record" will be loaded by default.
[     9.868] (II) "dri" will be loaded by default.
[     9.868] (II) "dri2" will be loaded by default.
[     9.868] (II) LoadModule: "extmod"
[     9.896] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.896] (II) Module extmod: vendor="X.Org Foundation"
[     9.896]     compiled for 1.11.3, module version = 1.0.0
[     9.896]     Module class: X.Org Server Extension
[     9.896]     ABI class: X.Org Server Extension, version 6.0
[     9.896] (II) Loading extension MIT-SCREEN-SAVER
[     9.896] (II) Loading extension XFree86-VidModeExtension
[     9.896] (II) Loading extension XFree86-DGA
[     9.896] (II) Loading extension DPMS
[     9.896] (II) Loading extension XVideo
[     9.896] (II) Loading extension XVideo-MotionCompensation
[     9.896] (II) Loading extension X-Resource
[     9.896] (II) LoadModule: "dbe"
[     9.896] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.896] (II) Module dbe: vendor="X.Org Foundation"
[     9.896]     compiled for 1.11.3, module version = 1.0.0
[     9.896]     Module class: X.Org Server Extension
[     9.896]     ABI class: X.Org Server Extension, version 6.0
[     9.896] (II) Loading extension DOUBLE-BUFFER
[     9.896] (II) LoadModule: "glx"
[     9.896] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.896] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     9.896]     compiled for 6.9.0, module version = 1.0.0
[     9.897] (II) Loading extension GLX
[     9.897] (II) LoadModule: "record"
[     9.897] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.897] (II) Module record: vendor="X.Org Foundation"
[     9.897]     compiled for 1.11.3, module version = 1.13.0
[     9.897]     Module class: X.Org Server Extension
[     9.897]     ABI class: X.Org Server Extension, version 6.0
[     9.897] (II) Loading extension RECORD
[     9.897] (II) LoadModule: "dri"
[     9.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.897] (II) Module dri: vendor="X.Org Foundation"
[     9.897]     compiled for 1.11.3, module version = 1.0.0
[     9.897]     ABI class: X.Org Server Extension, version 6.0
[     9.897] (II) Loading extension XFree86-DRI
[     9.897] (II) LoadModule: "dri2"
[     9.897] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.897] (II) Module dri2: vendor="X.Org Foundation"
[     9.897]     compiled for 1.11.3, module version = 1.2.0
[     9.897]     ABI class: X.Org Server Extension, version 6.0
[     9.897] (II) Loading extension DRI2
[     9.897] (II) LoadModule: "fglrx"
[     9.897] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[     9.908] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     9.908]     compiled for 1.4.99.906, module version = 13.25.5
[     9.909]     Module class: X.Org Video Driver
[     9.909] (II) Loading sub module "fglrxdrm"
[     9.909] (II) LoadModule: "fglrxdrm"
[     9.909] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[     9.909] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     9.909]     compiled for 1.4.99.906, module version = 13.25.5
[     9.909] (II) AMD Proprietary Linux Driver Version Identifier:13.25.5
[     9.909] (II) AMD Proprietary Linux Driver Release Identifier: 13.251                               
[     9.909] (II) AMD Proprietary Linux Driver Build Date: Dec  6 2013 15:19:03
[     9.909] (++) using VT number 7

[     9.910] (WW) Falling back to old probe method for fglrx
[     9.929] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     9.930] ukiDynamicMajor: found major device number 250
[     9.930] ukiDynamicMajor: found major device number 250
[     9.930] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[     9.930] ukiOpenDevice: node name is /dev/ati/card0
[     9.930] ukiOpenDevice: open result is 8, (OK)
[    10.416] ukiOpenByBusid: ukiOpenMinor returns 8
[    10.416] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    10.416] ukiOpenDevice: node name is /dev/ati/card1
[    10.898] ukiOpenDevice: open result is 8, (OK)
[    10.898] ukiOpenByBusid: ukiOpenMinor returns 8
[    10.898] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    10.898] ukiOpenDevice: node name is /dev/ati/card2
[    11.382] ukiOpenDevice: open result is 8, (OK)
[    11.382] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.382] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    11.399] ukiDynamicMajor: found major device number 250
[    11.399] ukiDynamicMajor: found major device number 250
[    11.399] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    11.399] ukiOpenDevice: node name is /dev/ati/card0
[    11.399] ukiOpenDevice: open result is 8, (OK)
[    11.399] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.399] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.399] ukiOpenDevice: node name is /dev/ati/card1
[    11.399] ukiOpenDevice: open result is 8, (OK)
[    11.399] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.399] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    11.400] ukiDynamicMajor: found major device number 250
[    11.401] ukiDynamicMajor: found major device number 250
[    11.401] ukiOpenByBusid: Searching for BusID PCI:5:0:0
[    11.401] ukiOpenDevice: node name is /dev/ati/card0
[    11.401] ukiOpenDevice: open result is 8, (OK)
[    11.401] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.401] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.401] ukiOpenDevice: node name is /dev/ati/card1
[    11.401] ukiOpenDevice: open result is 8, (OK)
[    11.401] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.401] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    11.401] ukiOpenDevice: node name is /dev/ati/card2
[    11.401] ukiOpenDevice: open result is 8, (OK)
[    11.401] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.401] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    11.401] ukiOpenDevice: node name is /dev/ati/card3
[    11.899] ukiOpenDevice: open result is 8, (OK)
[    11.899] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.899] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    11.899] ukiDynamicMajor: found major device number 250
[    11.899] ukiDynamicMajor: found major device number 250
[    11.899] ukiOpenByBusid: Searching for BusID PCI:6:0:0
[    11.899] ukiOpenDevice: node name is /dev/ati/card0
[    11.899] ukiOpenDevice: open result is 8, (OK)
[    11.899] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.899] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.899] ukiOpenDevice: node name is /dev/ati/card1
[    11.899] ukiOpenDevice: open result is 8, (OK)
[    11.899] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.899] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    11.899] ukiOpenDevice: node name is /dev/ati/card2
[    11.899] ukiOpenDevice: open result is 8, (OK)
[    11.899] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.899] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    11.899] ukiOpenDevice: node name is /dev/ati/card3
[    11.899] ukiOpenDevice: open result is 8, (OK)
[    11.899] ukiOpenByBusid: ukiOpenMinor returns 8
[    11.899] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    11.899] ukiOpenDevice: node name is /dev/ati/card4
[    12.398] ukiOpenDevice: open result is 8, (OK)
[    12.398] ukiOpenByBusid: ukiOpenMinor returns 8
[    12.398] ukiOpenByBusid: ukiGetBusid reports PCI:6:0:0
[    12.398] ukiDynamicMajor: found major device number 250
[    12.398] ukiDynamicMajor: found major device number 250
[    12.398] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.398] ukiOpenDevice: node name is /dev/ati/card0
[    12.398] ukiOpenDevice: open result is 8, (OK)
[    12.398] ukiOpenByBusid: ukiOpenMinor returns 8
[    12.398] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.462] (--) Chipset Supported AMD Graphics Processor (0x6798) found
[    12.462] (--) Chipset Supported AMD Graphics Processor (0x679A) found
[    12.462] (--) Chipset Supported AMD Graphics Processor (0x679A) found
[    12.462] (--) Chipset Supported AMD Graphics Processor (0x679A) found
[    12.462] (--) Chipset Supported AMD Graphics Processor (0x679A) found
[    12.484] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    12.484] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    12.484] (WW) fglrx: No matching Device section for instance (BusID PCI:0@3:0:1) found
[    12.484] (WW) fglrx: No matching Device section for instance (BusID PCI:0@5:0:1) found
[    12.484] (WW) fglrx: No matching Device section for instance (BusID PCI:0@6:0:1) found
[    12.496] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    12.496] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.496] (II) fglrx(0): pEnt->device->identifier=0x7f9f9beb0310
[    12.496] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    12.496] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.496] (II) fglrx(1): pEnt->device->identifier=0x7f9f9beaf9e0
[    12.496] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    12.496] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.496] (II) fglrx(2): pEnt->device->identifier=0x7f9f9beaf6d0
[    12.496] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    12.496] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.496] (II) fglrx(3): pEnt->device->identifier=0x7f9f9beafcf0
[    12.496] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    12.496] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.496] (II) fglrx(4): pEnt->device->identifier=0x7f9f9beb0000
[    12.496] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    12.496] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    12.496] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.496] (==) fglrx(0): Default visual is TrueColor
[    12.496] (**) fglrx(0): Option "DPMS" "true"
[    12.496] (==) fglrx(0): RGB weight 888
[    12.496] (II) fglrx(0): Using 8 bits per RGB 
[    12.496] (==) fglrx(0): Buffer Tiling is ON
[    12.496] (II) Loading sub module "fglrxdrm"
[    12.496] (II) LoadModule: "fglrxdrm"
[    12.497] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.497] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.497]     compiled for 1.4.99.906, module version = 13.25.5
[    12.497] ukiDynamicMajor: found major device number 250
[    12.497] ukiDynamicMajor: found major device number 250
[    12.497] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[    12.497] ukiOpenDevice: node name is /dev/ati/card0
[    12.497] ukiOpenDevice: open result is 10, (OK)
[    12.497] ukiOpenByBusid: ukiOpenMinor returns 10
[    12.497] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.498] ukiOpenDevice: node name is /dev/ati/card1
[    12.498] ukiOpenDevice: open result is 10, (OK)
[    12.498] ukiOpenByBusid: ukiOpenMinor returns 10
[    12.498] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.498] ukiOpenDevice: node name is /dev/ati/card2
[    12.498] ukiOpenDevice: open result is 10, (OK)
[    12.498] ukiOpenByBusid: ukiOpenMinor returns 10
[    12.498] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    12.498] (**) fglrx(0): NoAccel = NO
[    12.498] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    12.498] (--) fglrx(0): Chipset: "AMD Radeon HD 7900 Series " (Chipset = 0x679a)
[    12.498] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x201c)
[    12.498] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    12.498] (--) fglrx(0): Linear framebuffer (phys) at 0xa0000000
[    12.498] (--) fglrx(0): MMIO registers at 0xb0000000
[    12.498] (--) fglrx(0): I/O port at 0x0000c000
[    12.498] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    12.498] (II) fglrx(0): AC Adapter is used
[    12.499] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    12.499] (--) fglrx(0): Video RAM: 3145728 kByte, Type: GDDR5
[    12.499] (II) fglrx(0): PCIE card detected
[    12.499] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    12.499] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    12.499] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0xc0000000)
[    12.499] (II) fglrx(0): RandR 1.2 support is enabled!
[    12.499] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    12.499] (==) fglrx(0): Center Mode is disabled 
[    12.499] (II) Loading sub module "fb"
[    12.499] (II) LoadModule: "fb"
[    12.499] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.521] (II) Module fb: vendor="X.Org Foundation"
[    12.521]     compiled for 1.11.3, module version = 1.0.0
[    12.521]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.521] (II) Loading sub module "ddc"
[    12.521] (II) LoadModule: "ddc"
[    12.521] (II) Module "ddc" already built-in
[    12.640] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    12.640] (II) fglrx(0): Output DFP2 has no monitor section
[    12.640] (II) fglrx(0): Output DFP3 has no monitor section
[    12.640] (II) fglrx(0): Output DFP4 has no monitor section
[    12.640] (II) fglrx(0): Output DFP5 has no monitor section
[    12.640] (II) fglrx(0): Output DFP6 has no monitor section
[    12.640] (II) fglrx(0): Output DFP7 has no monitor section
[    12.640] (II) fglrx(0): Output DFP8 has no monitor section
[    12.640] (II) fglrx(0): Output DFP9 has no monitor section
[    12.640] (II) fglrx(0): Output DFP10 has no monitor section
[    12.640] (II) fglrx(0): Output CRT1 has no monitor section
[    12.640] (II) Loading sub module "ddc"
[    12.640] (II) LoadModule: "ddc"
[    12.640] (II) Module "ddc" already built-in
[    12.640] (II) fglrx(0): Connected Display0: CRT1
[    12.641] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    12.641] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    12.641] (II) fglrx(0): EDID for output DFP1
[    12.641] (II) fglrx(0): EDID for output DFP2
[    12.641] (II) fglrx(0): EDID for output DFP3
[    12.641] (II) fglrx(0): EDID for output DFP4
[    12.641] (II) fglrx(0): EDID for output DFP5
[    12.641] (II) fglrx(0): EDID for output DFP6
[    12.641] (II) fglrx(0): EDID for output DFP7
[    12.641] (II) fglrx(0): EDID for output DFP8
[    12.641] (II) fglrx(0): EDID for output DFP9
[    12.641] (II) fglrx(0): EDID for output DFP10
[    12.641] (II) fglrx(0): Cannot get EDID information for CRT1
[    12.641] (II) fglrx(0): EDID for output CRT1
[    12.641] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[    12.641] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[    12.641] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[    12.641] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1680x1050" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1680x1050" (unknown reason)
[    12.641] (II) fglrx(0): Not using mode "1680x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1680x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1680x1050" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1792x1344" (hsync out of range)
[    12.641] (II) fglrx(0): Not using mode "1792x1344" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1792x1344" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1856x1392" (hsync out of range)
[    12.641] (II) fglrx(0): Not using mode "1856x1392" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1856x1392" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1200" (monitor doesn't support reduced blanking)
[    12.641] (II) fglrx(0): Not using mode "1920x1200" (unknown reason)
[    12.641] (II) fglrx(0): Not using mode "1920x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1200" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1440" (hsync out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1440" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "1920x1440" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "2560x1600" (hsync out of range)
[    12.641] (II) fglrx(0): Not using mode "2560x1600" (hsync out of range)
[    12.641] (II) fglrx(0): Not using mode "2560x1600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "2560x1600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Not using mode "2560x1600" (vrefresh out of range)
[    12.641] (II) fglrx(0): Printing probed modes for output CRT1
[    12.641] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    12.641] (II) fglrx(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    12.641] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    12.641] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.641] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.641] (II) fglrx(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    12.641] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    12.641] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.641] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    12.641] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    12.641] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    12.641] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.641] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.641] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.641] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.641] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.641] (II) fglrx(0): Output DFP1 disconnected
[    12.641] (II) fglrx(0): Output DFP2 disconnected
[    12.641] (II) fglrx(0): Output DFP3 disconnected
[    12.641] (II) fglrx(0): Output DFP4 disconnected
[    12.641] (II) fglrx(0): Output DFP5 disconnected
[    12.641] (II) fglrx(0): Output DFP6 disconnected
[    12.641] (II) fglrx(0): Output DFP7 disconnected
[    12.641] (II) fglrx(0): Output DFP8 disconnected
[    12.641] (II) fglrx(0): Output DFP9 disconnected
[    12.641] (II) fglrx(0): Output DFP10 disconnected
[    12.641] (II) fglrx(0): Output CRT1 connected
[    12.641] (II) fglrx(0): Using exact sizes for initial modes
[    12.641] (II) fglrx(0): Output CRT1 using initial mode 1600x1200
[    12.641] (II) fglrx(0): DPI set to (96, 96)
[    12.641] (II) fglrx(0): Eyefinity capable adapter detected.
[    12.641] (II) fglrx(0): Adapter AMD Radeon HD 7900 Series  has 6 configurable heads and 1 displays connected.
[    12.641] (==) fglrx(0):  PseudoColor visuals disabled
[    12.641] (II) Loading sub module "ramdac"
[    12.641] (II) LoadModule: "ramdac"
[    12.641] (II) Module "ramdac" already built-in
[    12.641] (==) fglrx(0): NoDRI = NO
[    12.641] (==) fglrx(0): Capabilities: 0x00000000
[    12.641] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    12.641] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.641] (==) fglrx(0): UseFastTLS=0
[    12.641] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    12.641] (II) fglrx(1): === [xdl_xs111_atiddxPreInit] === begin
[    12.642] (**) fglrx(1): Depth 24, (--) framebuffer bpp 32
[    12.642] (II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.642] (==) fglrx(1): Default visual is TrueColor
[    12.642] (**) fglrx(1): Option "DPMS" "true"
[    12.642] (==) fglrx(1): RGB weight 888
[    12.642] (II) fglrx(1): Using 8 bits per RGB 
[    12.642] (==) fglrx(1): Buffer Tiling is ON
[    12.642] (II) Loading sub module "fglrxdrm"
[    12.642] (II) LoadModule: "fglrxdrm"
[    12.642] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.642] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.642]     compiled for 1.4.99.906, module version = 13.25.5
[    12.643] ukiDynamicMajor: found major device number 250
[    12.643] ukiDynamicMajor: found major device number 250
[    12.643] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    12.643] ukiOpenDevice: node name is /dev/ati/card0
[    12.643] ukiOpenDevice: open result is 11, (OK)
[    12.643] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.643] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.643] ukiOpenDevice: node name is /dev/ati/card1
[    12.643] ukiOpenDevice: open result is 11, (OK)
[    12.643] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.643] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.643] (WW) fglrx(1): Unable to register ADL handler for 0x00C00000
[    12.643] (**) fglrx(1): NoAccel = NO
[    12.643] (**) fglrx(1): AMD 2D Acceleration Architecture enabled
[    12.643] (--) fglrx(1): Chipset: "AMD Radeon HD 7900 Series " (Chipset = 0x679a)
[    12.643] (--) fglrx(1): (PciSubVendor = 0x1787, PciSubDevice = 0x201c)
[    12.643] (==) fglrx(1): board vendor info: third party graphics adapter - NOT original AMD
[    12.643] (--) fglrx(1): Linear framebuffer (phys) at 0xc0000000
[    12.643] (--) fglrx(1): MMIO registers at 0xd0000000
[    12.643] (--) fglrx(1): I/O port at 0x0000d000
[    12.643] (==) fglrx(1): ROM-BIOS at 0x000c0000
[    12.643] (II) fglrx(0): AC Adapter is used
[    12.643] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    12.643] (--) fglrx(1): Video RAM: 3145728 kByte, Type: GDDR5
[    12.643] (II) fglrx(1): PCIE card detected
[    12.643] (--) fglrx(1): Using per-process page tables (PPPT) as GART.
[    12.643] (WW) fglrx(1): board is an unknown third party board, chipset is supported
[    12.643] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0xc0000000)
[    12.643] (II) fglrx(1): RandR 1.2 support is enabled!
[    12.643] (II) fglrx(1): RandR 1.2 rotation support is enabled!
[    12.643] (==) fglrx(1): Center Mode is disabled 
[    12.643] (II) Loading sub module "fb"
[    12.643] (II) LoadModule: "fb"
[    12.643] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.643] (II) Module fb: vendor="X.Org Foundation"
[    12.643]     compiled for 1.11.3, module version = 1.0.0
[    12.643]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.643] (II) Loading sub module "ddc"
[    12.643] (II) LoadModule: "ddc"
[    12.643] (II) Module "ddc" already built-in
[    12.704] (II) fglrx(1): Output DFP1 using monitor section aticonfig-Monitor[1]-0
[    12.704] (II) fglrx(1): Output DFP2 has no monitor section
[    12.704] (II) fglrx(1): Output DFP3 has no monitor section
[    12.704] (II) fglrx(1): Output DFP4 has no monitor section
[    12.704] (II) fglrx(1): Output DFP5 has no monitor section
[    12.704] (II) fglrx(1): Output DFP6 has no monitor section
[    12.704] (II) fglrx(1): Output DFP7 has no monitor section
[    12.704] (II) fglrx(1): Output DFP8 has no monitor section
[    12.704] (II) fglrx(1): Output DFP9 has no monitor section
[    12.704] (II) fglrx(1): Output DFP10 has no monitor section
[    12.704] (II) fglrx(1): Output CRT1 has no monitor section
[    12.704] (II) Loading sub module "ddc"
[    12.704] (II) LoadModule: "ddc"
[    12.705] (II) Module "ddc" already built-in
[    12.705] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    12.705] (II) fglrx(1): EDID for output DFP1
[    12.705] (II) fglrx(1): EDID for output DFP2
[    12.705] (II) fglrx(1): EDID for output DFP3
[    12.705] (II) fglrx(1): EDID for output DFP4
[    12.705] (II) fglrx(1): EDID for output DFP5
[    12.705] (II) fglrx(1): EDID for output DFP6
[    12.705] (II) fglrx(1): EDID for output DFP7
[    12.705] (II) fglrx(1): EDID for output DFP8
[    12.705] (II) fglrx(1): EDID for output DFP9
[    12.705] (II) fglrx(1): EDID for output DFP10
[    12.705] (II) fglrx(1): Not using mode "640x350" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "640x400" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "720x400" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "640x480" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "640x480" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "640x480" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "800x600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "800x600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "800x600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "800x600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "800x600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "848x480" (unknown reason)
[    12.705] (II) fglrx(1): Not using mode "1024x768i" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1024x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1024x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1024x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1024x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1152x864" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1280x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1280x800" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x800" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x800" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x960" (unknown reason)
[    12.705] (II) fglrx(1): Not using mode "1280x960" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x960" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x1024" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x1024" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1280x1024" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1360x768" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1400x1050" (unknown reason)
[    12.705] (II) fglrx(1): Not using mode "1400x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1400x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1400x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1440x900" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1440x900" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1440x900" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1600x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1600x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1600x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1600x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1600x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1680x1050" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1680x1050" (unknown reason)
[    12.705] (II) fglrx(1): Not using mode "1680x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1680x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1680x1050" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1792x1344" (hsync out of range)
[    12.705] (II) fglrx(1): Not using mode "1792x1344" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1792x1344" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1856x1392" (hsync out of range)
[    12.705] (II) fglrx(1): Not using mode "1856x1392" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1856x1392" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1200" (monitor doesn't support reduced blanking)
[    12.705] (II) fglrx(1): Not using mode "1920x1200" (unknown reason)
[    12.705] (II) fglrx(1): Not using mode "1920x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1200" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1440" (hsync out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1440" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "1920x1440" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "2560x1600" (hsync out of range)
[    12.705] (II) fglrx(1): Not using mode "2560x1600" (hsync out of range)
[    12.705] (II) fglrx(1): Not using mode "2560x1600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "2560x1600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Not using mode "2560x1600" (vrefresh out of range)
[    12.705] (II) fglrx(1): Printing probed modes for output CRT1
[    12.705] (II) fglrx(1): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    12.705] (II) fglrx(1): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    12.705] (II) fglrx(1): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    12.705] (II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.705] (II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.705] (II) fglrx(1): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    12.705] (II) fglrx(1): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    12.705] (II) fglrx(1): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.705] (II) fglrx(1): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    12.705] (II) fglrx(1): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    12.705] (II) fglrx(1): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    12.705] (II) fglrx(1): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.705] (II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.705] (II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.705] (II) fglrx(1): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.705] (II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.705] (II) fglrx(1): Output DFP1 disconnected
[    12.705] (II) fglrx(1): Output DFP2 disconnected
[    12.705] (II) fglrx(1): Output DFP3 disconnected
[    12.705] (II) fglrx(1): Output DFP4 disconnected
[    12.705] (II) fglrx(1): Output DFP5 disconnected
[    12.705] (II) fglrx(1): Output DFP6 disconnected
[    12.705] (II) fglrx(1): Output DFP7 disconnected
[    12.705] (II) fglrx(1): Output DFP8 disconnected
[    12.705] (II) fglrx(1): Output DFP9 disconnected
[    12.705] (II) fglrx(1): Output DFP10 disconnected
[    12.705] (II) fglrx(1): Output CRT1 connected
[    12.705] (II) fglrx(1): Using exact sizes for initial modes
[    12.705] (II) fglrx(1): Output CRT1 using initial mode 1600x1200
[    12.705] (II) fglrx(1): DPI set to (96, 96)
[    12.705] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    12.705] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    12.705] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    12.705] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    12.705] (II) fglrx(1): Eyefinity capable adapter detected.
[    12.705] (II) fglrx(1): Adapter AMD Radeon HD 7900 Series  has 6 configurable heads and 0 displays connected.
[    12.705] (==) fglrx(1):  PseudoColor visuals disabled
[    12.705] (II) Loading sub module "ramdac"
[    12.705] (II) LoadModule: "ramdac"
[    12.705] (II) Module "ramdac" already built-in
[    12.705] (==) fglrx(1): NoDRI = NO
[    12.705] (==) fglrx(1): Capabilities: 0x00000000
[    12.705] (==) fglrx(1): CapabilitiesEx: 0x00000000
[    12.705] (==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.705] (==) fglrx(1): UseFastTLS=0
[    12.705] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    12.705] (II) fglrx(2): === [xdl_xs111_atiddxPreInit] === begin
[    12.705] (**) fglrx(2): Depth 24, (--) framebuffer bpp 32
[    12.705] (II) fglrx(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.705] (==) fglrx(2): Default visual is TrueColor
[    12.705] (**) fglrx(2): Option "DPMS" "true"
[    12.705] (==) fglrx(2): RGB weight 888
[    12.705] (II) fglrx(2): Using 8 bits per RGB 
[    12.705] (==) fglrx(2): Buffer Tiling is ON
[    12.705] (II) Loading sub module "fglrxdrm"
[    12.705] (II) LoadModule: "fglrxdrm"
[    12.706] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.706] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.706]     compiled for 1.4.99.906, module version = 13.25.5
[    12.707] ukiDynamicMajor: found major device number 250
[    12.707] ukiDynamicMajor: found major device number 250
[    12.707] ukiOpenByBusid: Searching for BusID PCI:5:0:0
[    12.707] ukiOpenDevice: node name is /dev/ati/card0
[    12.707] ukiOpenDevice: open result is 12, (OK)
[    12.707] ukiOpenByBusid: ukiOpenMinor returns 12
[    12.707] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.707] ukiOpenDevice: node name is /dev/ati/card1
[    12.707] ukiOpenDevice: open result is 12, (OK)
[    12.707] ukiOpenByBusid: ukiOpenMinor returns 12
[    12.707] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.707] ukiOpenDevice: node name is /dev/ati/card2
[    12.707] ukiOpenDevice: open result is 12, (OK)
[    12.707] ukiOpenByBusid: ukiOpenMinor returns 12
[    12.707] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    12.707] ukiOpenDevice: node name is /dev/ati/card3
[    12.707] ukiOpenDevice: open result is 12, (OK)
[    12.707] ukiOpenByBusid: ukiOpenMinor returns 12
[    12.707] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    12.707] (WW) fglrx(2): Unable to register ADL handler for 0x00C00000
[    12.707] (**) fglrx(2): NoAccel = NO
[    12.707] (**) fglrx(2): AMD 2D Acceleration Architecture enabled
[    12.707] (--) fglrx(2): Chipset: "AMD Radeon HD 7900 Series " (Chipset = 0x679a)
[    12.707] (--) fglrx(2): (PciSubVendor = 0x1682, PciSubDevice = 0x3221)
[    12.707] (==) fglrx(2): board vendor info: third party graphics adapter - NOT original AMD
[    12.707] (--) fglrx(2): Linear framebuffer (phys) at 0x80000000
[    12.707] (--) fglrx(2): MMIO registers at 0x90000000
[    12.707] (--) fglrx(2): I/O port at 0x0000b000
[    12.707] (==) fglrx(2): ROM-BIOS at 0x000c0000
[    12.707] (II) fglrx(0): AC Adapter is used
[    12.707] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    12.707] (--) fglrx(2): Video RAM: 3145728 kByte, Type: GDDR5
[    12.707] (II) fglrx(2): PCIE card detected
[    12.707] (--) fglrx(2): Using per-process page tables (PPPT) as GART.
[    12.707] (WW) fglrx(2): board is an unknown third party board, chipset is supported
[    12.707] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0xc0000000)
[    12.707] (II) fglrx(2): RandR 1.2 support is enabled!
[    12.707] (II) fglrx(2): RandR 1.2 rotation support is enabled!
[    12.707] (==) fglrx(2): Center Mode is disabled 
[    12.707] (II) Loading sub module "fb"
[    12.707] (II) LoadModule: "fb"
[    12.707] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.707] (II) Module fb: vendor="X.Org Foundation"
[    12.707]     compiled for 1.11.3, module version = 1.0.0
[    12.707]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.707] (II) Loading sub module "ddc"
[    12.707] (II) LoadModule: "ddc"
[    12.707] (II) Module "ddc" already built-in
[    12.774] (II) fglrx(2): Output DFP1 using monitor section aticonfig-Monitor[2]-0
[    12.775] (II) fglrx(2): Output DFP2 has no monitor section
[    12.775] (II) fglrx(2): Output DFP3 has no monitor section
[    12.775] (II) fglrx(2): Output DFP4 has no monitor section
[    12.775] (II) fglrx(2): Output DFP5 has no monitor section
[    12.775] (II) fglrx(2): Output DFP6 has no monitor section
[    12.775] (II) fglrx(2): Output DFP7 has no monitor section
[    12.775] (II) fglrx(2): Output DFP8 has no monitor section
[    12.775] (II) fglrx(2): Output DFP9 has no monitor section
[    12.775] (II) fglrx(2): Output DFP10 has no monitor section
[    12.775] (II) fglrx(2): Output DFP11 has no monitor section
[    12.775] (II) fglrx(2): Output CRT1 has no monitor section
[    12.775] (II) Loading sub module "ddc"
[    12.775] (II) LoadModule: "ddc"
[    12.775] (II) Module "ddc" already built-in
[    12.775] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    12.775] (II) fglrx(2): EDID for output DFP1
[    12.775] (II) fglrx(2): EDID for output DFP2
[    12.775] (II) fglrx(2): EDID for output DFP3
[    12.775] (II) fglrx(2): EDID for output DFP4
[    12.775] (II) fglrx(2): EDID for output DFP5
[    12.775] (II) fglrx(2): EDID for output DFP6
[    12.775] (II) fglrx(2): EDID for output DFP7
[    12.775] (II) fglrx(2): EDID for output DFP8
[    12.775] (II) fglrx(2): EDID for output DFP9
[    12.775] (II) fglrx(2): EDID for output DFP10
[    12.775] (II) fglrx(2): EDID for output DFP11
[    12.775] (II) fglrx(2): Not using mode "640x350" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "640x400" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "720x400" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "640x480" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "640x480" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "640x480" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "800x600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "800x600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "800x600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "800x600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "800x600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "848x480" (unknown reason)
[    12.775] (II) fglrx(2): Not using mode "1024x768i" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1024x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1024x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1024x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1024x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1152x864" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1280x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1280x800" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x800" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x800" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x960" (unknown reason)
[    12.775] (II) fglrx(2): Not using mode "1280x960" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x960" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x1024" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x1024" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1280x1024" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1360x768" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1400x1050" (unknown reason)
[    12.775] (II) fglrx(2): Not using mode "1400x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1400x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1400x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1440x900" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1440x900" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1440x900" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1600x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1600x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1600x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1600x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1600x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1680x1050" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1680x1050" (unknown reason)
[    12.775] (II) fglrx(2): Not using mode "1680x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1680x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1680x1050" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1792x1344" (hsync out of range)
[    12.775] (II) fglrx(2): Not using mode "1792x1344" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1792x1344" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1856x1392" (hsync out of range)
[    12.775] (II) fglrx(2): Not using mode "1856x1392" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1856x1392" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1200" (monitor doesn't support reduced blanking)
[    12.775] (II) fglrx(2): Not using mode "1920x1200" (unknown reason)
[    12.775] (II) fglrx(2): Not using mode "1920x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1200" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1440" (hsync out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1440" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "1920x1440" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "2560x1600" (hsync out of range)
[    12.775] (II) fglrx(2): Not using mode "2560x1600" (hsync out of range)
[    12.775] (II) fglrx(2): Not using mode "2560x1600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "2560x1600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Not using mode "2560x1600" (vrefresh out of range)
[    12.775] (II) fglrx(2): Printing probed modes for output CRT1
[    12.775] (II) fglrx(2): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    12.775] (II) fglrx(2): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    12.775] (II) fglrx(2): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    12.775] (II) fglrx(2): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.775] (II) fglrx(2): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.775] (II) fglrx(2): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    12.775] (II) fglrx(2): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    12.775] (II) fglrx(2): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.775] (II) fglrx(2): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    12.775] (II) fglrx(2): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    12.775] (II) fglrx(2): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    12.775] (II) fglrx(2): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.775] (II) fglrx(2): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.775] (II) fglrx(2): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.775] (II) fglrx(2): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.775] (II) fglrx(2): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.775] (II) fglrx(2): Output DFP1 disconnected
[    12.775] (II) fglrx(2): Output DFP2 disconnected
[    12.775] (II) fglrx(2): Output DFP3 disconnected
[    12.775] (II) fglrx(2): Output DFP4 disconnected
[    12.775] (II) fglrx(2): Output DFP5 disconnected
[    12.775] (II) fglrx(2): Output DFP6 disconnected
[    12.775] (II) fglrx(2): Output DFP7 disconnected
[    12.775] (II) fglrx(2): Output DFP8 disconnected
[    12.775] (II) fglrx(2): Output DFP9 disconnected
[    12.775] (II) fglrx(2): Output DFP10 disconnected
[    12.775] (II) fglrx(2): Output DFP11 disconnected
[    12.775] (II) fglrx(2): Output CRT1 connected
[    12.775] (II) fglrx(2): Using exact sizes for initial modes
[    12.775] (II) fglrx(2): Output CRT1 using initial mode 1600x1200
[    12.775] (II) fglrx(2): DPI set to (96, 96)
[    12.775] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    12.775] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    12.775] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    12.775] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    12.775] (II) fglrx(2): Eyefinity capable adapter detected.
[    12.775] (II) fglrx(2): Adapter AMD Radeon HD 7900 Series  has 6 configurable heads and 0 displays connected.
[    12.775] (==) fglrx(2):  PseudoColor visuals disabled
[    12.775] (II) Loading sub module "ramdac"
[    12.775] (II) LoadModule: "ramdac"
[    12.775] (II) Module "ramdac" already built-in
[    12.775] (==) fglrx(2): NoDRI = NO
[    12.775] (==) fglrx(2): Capabilities: 0x00000000
[    12.775] (==) fglrx(2): CapabilitiesEx: 0x00000000
[    12.775] (==) fglrx(2): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.775] (==) fglrx(2): UseFastTLS=0
[    12.775] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    12.775] (II) fglrx(3): === [xdl_xs111_atiddxPreInit] === begin
[    12.776] (**) fglrx(3): Depth 24, (--) framebuffer bpp 32
[    12.776] (II) fglrx(3): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.776] (==) fglrx(3): Default visual is TrueColor
[    12.776] (**) fglrx(3): Option "DPMS" "true"
[    12.776] (==) fglrx(3): RGB weight 888
[    12.776] (II) fglrx(3): Using 8 bits per RGB 
[    12.776] (==) fglrx(3): Buffer Tiling is ON
[    12.776] (II) Loading sub module "fglrxdrm"
[    12.776] (II) LoadModule: "fglrxdrm"
[    12.776] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.776] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.776]     compiled for 1.4.99.906, module version = 13.25.5
[    12.777] ukiDynamicMajor: found major device number 250
[    12.777] ukiDynamicMajor: found major device number 250
[    12.777] ukiOpenByBusid: Searching for BusID PCI:6:0:0
[    12.777] ukiOpenDevice: node name is /dev/ati/card0
[    12.777] ukiOpenDevice: open result is 13, (OK)
[    12.777] ukiOpenByBusid: ukiOpenMinor returns 13
[    12.777] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.777] ukiOpenDevice: node name is /dev/ati/card1
[    12.777] ukiOpenDevice: open result is 13, (OK)
[    12.777] ukiOpenByBusid: ukiOpenMinor returns 13
[    12.777] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.777] ukiOpenDevice: node name is /dev/ati/card2
[    12.777] ukiOpenDevice: open result is 13, (OK)
[    12.777] ukiOpenByBusid: ukiOpenMinor returns 13
[    12.777] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    12.777] ukiOpenDevice: node name is /dev/ati/card3
[    12.777] ukiOpenDevice: open result is 13, (OK)
[    12.777] ukiOpenByBusid: ukiOpenMinor returns 13
[    12.777] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    12.777] ukiOpenDevice: node name is /dev/ati/card4
[    12.777] ukiOpenDevice: open result is 13, (OK)
[    12.777] ukiOpenByBusid: ukiOpenMinor returns 13
[    12.777] ukiOpenByBusid: ukiGetBusid reports PCI:6:0:0
[    12.777] (WW) fglrx(3): Unable to register ADL handler for 0x00C00000
[    12.777] (**) fglrx(3): NoAccel = NO
[    12.777] (**) fglrx(3): AMD 2D Acceleration Architecture enabled
[    12.777] (--) fglrx(3): Chipset: "AMD Radeon HD 7900 Series " (Chipset = 0x679a)
[    12.777] (--) fglrx(3): (PciSubVendor = 0x1682, PciSubDevice = 0x3221)
[    12.777] (==) fglrx(3): board vendor info: third party graphics adapter - NOT original AMD
[    12.777] (--) fglrx(3): Linear framebuffer (phys) at 0x60000000
[    12.777] (--) fglrx(3): MMIO registers at 0x70000000
[    12.777] (--) fglrx(3): I/O port at 0x0000a000
[    12.777] (==) fglrx(3): ROM-BIOS at 0x000c0000
[    12.777] (II) fglrx(0): AC Adapter is used
[    12.777] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    12.777] (--) fglrx(3): Video RAM: 3145728 kByte, Type: GDDR5
[    12.777] (II) fglrx(3): PCIE card detected
[    12.777] (--) fglrx(3): Using per-process page tables (PPPT) as GART.
[    12.777] (WW) fglrx(3): board is an unknown third party board, chipset is supported
[    12.777] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0xc0000000)
[    12.777] (II) fglrx(3): RandR 1.2 support is enabled!
[    12.777] (II) fglrx(3): RandR 1.2 rotation support is enabled!
[    12.777] (==) fglrx(3): Center Mode is disabled 
[    12.777] (II) Loading sub module "fb"
[    12.777] (II) LoadModule: "fb"
[    12.778] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.778] (II) Module fb: vendor="X.Org Foundation"
[    12.778]     compiled for 1.11.3, module version = 1.0.0
[    12.778]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.778] (II) Loading sub module "ddc"
[    12.778] (II) LoadModule: "ddc"
[    12.778] (II) Module "ddc" already built-in
[    12.844] (II) fglrx(3): Output DFP1 using monitor section aticonfig-Monitor[3]-0
[    12.844] (II) fglrx(3): Output DFP2 has no monitor section
[    12.844] (II) fglrx(3): Output DFP3 has no monitor section
[    12.844] (II) fglrx(3): Output DFP4 has no monitor section
[    12.844] (II) fglrx(3): Output DFP5 has no monitor section
[    12.844] (II) fglrx(3): Output DFP6 has no monitor section
[    12.844] (II) fglrx(3): Output DFP7 has no monitor section
[    12.844] (II) fglrx(3): Output DFP8 has no monitor section
[    12.844] (II) fglrx(3): Output DFP9 has no monitor section
[    12.844] (II) fglrx(3): Output DFP10 has no monitor section
[    12.844] (II) fglrx(3): Output DFP11 has no monitor section
[    12.844] (II) fglrx(3): Output CRT1 has no monitor section
[    12.844] (II) Loading sub module "ddc"
[    12.844] (II) LoadModule: "ddc"
[    12.844] (II) Module "ddc" already built-in
[    12.844] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    12.844] (II) fglrx(3): EDID for output DFP1
[    12.844] (II) fglrx(3): EDID for output DFP2
[    12.844] (II) fglrx(3): EDID for output DFP3
[    12.844] (II) fglrx(3): EDID for output DFP4
[    12.844] (II) fglrx(3): EDID for output DFP5
[    12.844] (II) fglrx(3): EDID for output DFP6
[    12.844] (II) fglrx(3): EDID for output DFP7
[    12.844] (II) fglrx(3): EDID for output DFP8
[    12.844] (II) fglrx(3): EDID for output DFP9
[    12.844] (II) fglrx(3): EDID for output DFP10
[    12.844] (II) fglrx(3): EDID for output DFP11
[    12.844] (II) fglrx(3): Not using mode "640x350" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "640x400" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "720x400" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "640x480" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "640x480" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "640x480" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "800x600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "800x600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "800x600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "800x600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "800x600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "848x480" (unknown reason)
[    12.844] (II) fglrx(3): Not using mode "1024x768i" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1024x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1024x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1024x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1024x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1152x864" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1280x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1280x800" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x800" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x800" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x960" (unknown reason)
[    12.844] (II) fglrx(3): Not using mode "1280x960" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x960" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x1024" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x1024" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1280x1024" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1360x768" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1400x1050" (unknown reason)
[    12.844] (II) fglrx(3): Not using mode "1400x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1400x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1400x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1440x900" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1440x900" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1440x900" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1600x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1600x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1600x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1600x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1600x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1680x1050" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1680x1050" (unknown reason)
[    12.844] (II) fglrx(3): Not using mode "1680x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1680x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1680x1050" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1792x1344" (hsync out of range)
[    12.844] (II) fglrx(3): Not using mode "1792x1344" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1792x1344" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1856x1392" (hsync out of range)
[    12.844] (II) fglrx(3): Not using mode "1856x1392" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1856x1392" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1200" (monitor doesn't support reduced blanking)
[    12.844] (II) fglrx(3): Not using mode "1920x1200" (unknown reason)
[    12.844] (II) fglrx(3): Not using mode "1920x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1200" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1440" (hsync out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1440" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "1920x1440" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "2560x1600" (hsync out of range)
[    12.844] (II) fglrx(3): Not using mode "2560x1600" (hsync out of range)
[    12.844] (II) fglrx(3): Not using mode "2560x1600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "2560x1600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Not using mode "2560x1600" (vrefresh out of range)
[    12.844] (II) fglrx(3): Printing probed modes for output CRT1
[    12.844] (II) fglrx(3): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    12.844] (II) fglrx(3): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    12.845] (II) fglrx(3): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    12.845] (II) fglrx(3): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.845] (II) fglrx(3): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.845] (II) fglrx(3): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    12.845] (II) fglrx(3): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    12.845] (II) fglrx(3): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.845] (II) fglrx(3): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    12.845] (II) fglrx(3): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    12.845] (II) fglrx(3): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    12.845] (II) fglrx(3): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.845] (II) fglrx(3): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.845] (II) fglrx(3): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.845] (II) fglrx(3): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.845] (II) fglrx(3): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.845] (II) fglrx(3): Output DFP1 disconnected
[    12.845] (II) fglrx(3): Output DFP2 disconnected
[    12.845] (II) fglrx(3): Output DFP3 disconnected
[    12.845] (II) fglrx(3): Output DFP4 disconnected
[    12.845] (II) fglrx(3): Output DFP5 disconnected
[    12.845] (II) fglrx(3): Output DFP6 disconnected
[    12.845] (II) fglrx(3): Output DFP7 disconnected
[    12.845] (II) fglrx(3): Output DFP8 disconnected
[    12.845] (II) fglrx(3): Output DFP9 disconnected
[    12.845] (II) fglrx(3): Output DFP10 disconnected
[    12.845] (II) fglrx(3): Output DFP11 disconnected
[    12.845] (II) fglrx(3): Output CRT1 connected
[    12.845] (II) fglrx(3): Using exact sizes for initial modes
[    12.845] (II) fglrx(3): Output CRT1 using initial mode 1600x1200
[    12.845] (II) fglrx(3): DPI set to (96, 96)
[    12.845] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    12.845] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    12.845] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    12.845] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    12.845] (II) fglrx(3): Eyefinity capable adapter detected.
[    12.845] (II) fglrx(3): Adapter AMD Radeon HD 7900 Series  has 6 configurable heads and 0 displays connected.
[    12.845] (==) fglrx(3):  PseudoColor visuals disabled
[    12.845] (II) Loading sub module "ramdac"
[    12.845] (II) LoadModule: "ramdac"
[    12.845] (II) Module "ramdac" already built-in
[    12.845] (==) fglrx(3): NoDRI = NO
[    12.845] (==) fglrx(3): Capabilities: 0x00000000
[    12.845] (==) fglrx(3): CapabilitiesEx: 0x00000000
[    12.845] (==) fglrx(3): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.845] (==) fglrx(3): UseFastTLS=0
[    12.845] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    12.845] (II) fglrx(4): === [xdl_xs111_atiddxPreInit] === begin
[    12.845] (**) fglrx(4): Depth 24, (--) framebuffer bpp 32
[    12.845] (II) fglrx(4): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.845] (==) fglrx(4): Default visual is TrueColor
[    12.845] (**) fglrx(4): Option "DPMS" "true"
[    12.845] (==) fglrx(4): RGB weight 888
[    12.845] (II) fglrx(4): Using 8 bits per RGB 
[    12.845] (==) fglrx(4): Buffer Tiling is ON
[    12.845] (II) Loading sub module "fglrxdrm"
[    12.845] (II) LoadModule: "fglrxdrm"
[    12.845] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    12.845] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    12.845]     compiled for 1.4.99.906, module version = 13.25.5
[    12.846] ukiDynamicMajor: found major device number 250
[    12.846] ukiDynamicMajor: found major device number 250
[    12.846] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.846] ukiOpenDevice: node name is /dev/ati/card0
[    12.846] ukiOpenDevice: open result is 14, (OK)
[    12.846] ukiOpenByBusid: ukiOpenMinor returns 14
[    12.846] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.846] (WW) fglrx(4): Unable to register ADL handler for 0x00C00000
[    12.847] (**) fglrx(4): NoAccel = NO
[    12.847] (**) fglrx(4): AMD 2D Acceleration Architecture enabled
[    12.847] (--) fglrx(4): Chipset: "AMD Radeon HD 7900 Series" (Chipset = 0x6798)
[    12.847] (--) fglrx(4): (PciSubVendor = 0x1787, PciSubDevice = 0x3000)
[    12.847] (==) fglrx(4): board vendor info: third party graphics adapter - NOT original AMD
[    12.847] (--) fglrx(4): Linear framebuffer (phys) at 0xe0000000
[    12.847] (--) fglrx(4): MMIO registers at 0xf0000000
[    12.847] (--) fglrx(4): I/O port at 0x0000e000
[    12.847] (==) fglrx(4): ROM-BIOS at 0x000c0000
[    12.847] (II) fglrx(0): AC Adapter is used
[    12.847] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    12.847] (--) fglrx(4): Video RAM: 3145728 kByte, Type: GDDR5
[    12.847] (II) fglrx(4): PCIE card detected
[    12.847] (--) fglrx(4): Using per-process page tables (PPPT) as GART.
[    12.847] (WW) fglrx(4): board is an unknown third party board, chipset is supported
[    12.847] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0xc0000000)
[    12.847] (II) fglrx(4): RandR 1.2 support is enabled!
[    12.847] (II) fglrx(4): RandR 1.2 rotation support is enabled!
[    12.847] (==) fglrx(4): Center Mode is disabled 
[    12.847] (II) Loading sub module "fb"
[    12.847] (II) LoadModule: "fb"
[    12.847] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.847] (II) Module fb: vendor="X.Org Foundation"
[    12.847]     compiled for 1.11.3, module version = 1.0.0
[    12.847]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.847] (II) Loading sub module "ddc"
[    12.847] (II) LoadModule: "ddc"
[    12.847] (II) Module "ddc" already built-in
[    12.903] (II) fglrx(4): Output DFP1 using monitor section aticonfig-Monitor[4]-0
[    12.903] (II) fglrx(4): Output DFP2 has no monitor section
[    12.903] (II) fglrx(4): Output DFP3 has no monitor section
[    12.903] (II) fglrx(4): Output DFP4 has no monitor section
[    12.903] (II) fglrx(4): Output DFP5 has no monitor section
[    12.903] (II) fglrx(4): Output DFP6 has no monitor section
[    12.903] (II) fglrx(4): Output DFP7 has no monitor section
[    12.903] (II) fglrx(4): Output DFP8 has no monitor section
[    12.903] (II) fglrx(4): Output DFP9 has no monitor section
[    12.903] (II) fglrx(4): Output DFP10 has no monitor section
[    12.903] (II) fglrx(4): Output CRT1 has no monitor section
[    12.904] (II) Loading sub module "ddc"
[    12.904] (II) LoadModule: "ddc"
[    12.904] (II) Module "ddc" already built-in
[    12.904] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    12.904] (II) fglrx(4): EDID for output DFP1
[    12.904] (II) fglrx(4): EDID for output DFP2
[    12.904] (II) fglrx(4): EDID for output DFP3
[    12.904] (II) fglrx(4): EDID for output DFP4
[    12.904] (II) fglrx(4): EDID for output DFP5
[    12.904] (II) fglrx(4): EDID for output DFP6
[    12.904] (II) fglrx(4): EDID for output DFP7
[    12.904] (II) fglrx(4): EDID for output DFP8
[    12.904] (II) fglrx(4): EDID for output DFP9
[    12.904] (II) fglrx(4): EDID for output DFP10
[    12.904] (II) fglrx(4): Not using mode "640x350" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "640x400" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "720x400" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "640x480" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "640x480" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "640x480" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "800x600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "800x600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "800x600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "800x600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "800x600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "848x480" (unknown reason)
[    12.904] (II) fglrx(4): Not using mode "1024x768i" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1024x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1024x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1024x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1024x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1152x864" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1280x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1280x800" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x800" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x800" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x960" (unknown reason)
[    12.904] (II) fglrx(4): Not using mode "1280x960" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x960" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x1024" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x1024" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1280x1024" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1360x768" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1400x1050" (unknown reason)
[    12.904] (II) fglrx(4): Not using mode "1400x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1400x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1400x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1440x900" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1440x900" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1440x900" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1600x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1600x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1600x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1600x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1600x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1680x1050" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1680x1050" (unknown reason)
[    12.904] (II) fglrx(4): Not using mode "1680x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1680x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1680x1050" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1792x1344" (hsync out of range)
[    12.904] (II) fglrx(4): Not using mode "1792x1344" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1792x1344" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1856x1392" (hsync out of range)
[    12.904] (II) fglrx(4): Not using mode "1856x1392" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1856x1392" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1200" (monitor doesn't support reduced blanking)
[    12.904] (II) fglrx(4): Not using mode "1920x1200" (unknown reason)
[    12.904] (II) fglrx(4): Not using mode "1920x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1200" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1440" (hsync out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1440" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "1920x1440" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "2560x1600" (hsync out of range)
[    12.904] (II) fglrx(4): Not using mode "2560x1600" (hsync out of range)
[    12.904] (II) fglrx(4): Not using mode "2560x1600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "2560x1600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Not using mode "2560x1600" (vrefresh out of range)
[    12.904] (II) fglrx(4): Printing probed modes for output CRT1
[    12.904] (II) fglrx(4): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    12.904] (II) fglrx(4): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
[    12.904] (II) fglrx(4): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
[    12.904] (II) fglrx(4): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.904] (II) fglrx(4): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.904] (II) fglrx(4): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
[    12.904] (II) fglrx(4): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[    12.904] (II) fglrx(4): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    12.904] (II) fglrx(4): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    12.904] (II) fglrx(4): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    12.904] (II) fglrx(4): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    12.904] (II) fglrx(4): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.904] (II) fglrx(4): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.904] (II) fglrx(4): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.904] (II) fglrx(4): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.904] (II) fglrx(4): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.904] (II) fglrx(4): Output DFP1 disconnected
[    12.904] (II) fglrx(4): Output DFP2 disconnected
[    12.904] (II) fglrx(4): Output DFP3 disconnected
[    12.904] (II) fglrx(4): Output DFP4 disconnected
[    12.904] (II) fglrx(4): Output DFP5 disconnected
[    12.904] (II) fglrx(4): Output DFP6 disconnected
[    12.904] (II) fglrx(4): Output DFP7 disconnected
[    12.904] (II) fglrx(4): Output DFP8 disconnected
[    12.904] (II) fglrx(4): Output DFP9 disconnected
[    12.904] (II) fglrx(4): Output DFP10 disconnected
[    12.904] (II) fglrx(4): Output CRT1 connected
[    12.904] (II) fglrx(4): Using exact sizes for initial modes
[    12.904] (II) fglrx(4): Output CRT1 using initial mode 1600x1200
[    12.904] (II) fglrx(4): DPI set to (96, 96)
[    12.904] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    12.904] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    12.904] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    12.904] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    12.904] (II) fglrx(4): Eyefinity capable adapter detected.
[    12.904] (II) fglrx(4): Adapter AMD Radeon HD 7900 Series has 6 configurable heads and 0 displays connected.
[    12.904] (==) fglrx(4):  PseudoColor visuals disabled
[    12.904] (II) Loading sub module "ramdac"
[    12.904] (II) LoadModule: "ramdac"
[    12.904] (II) Module "ramdac" already built-in
[    12.904] (==) fglrx(4): NoDRI = NO
[    12.904] (==) fglrx(4): Capabilities: 0x00000000
[    12.904] (==) fglrx(4): CapabilitiesEx: 0x00000000
[    12.904] (==) fglrx(4): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.904] (==) fglrx(4): UseFastTLS=0
[    12.904] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    12.904] (--) Depth 24 pixmap format is 32 bpp
[    12.904] (II) Loading extension ATIFGLRXDRI
[    12.904] (II) fglrx(0): doing swlDriScreenInit
[    12.904] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    12.904] ukiDynamicMajor: found major device number 250
[    12.904] ukiDynamicMajor: found major device number 250
[    12.905] ukiDynamicMajor: found major device number 250
[    12.905] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[    12.905] ukiOpenDevice: node name is /dev/ati/card0
[    12.905] ukiOpenDevice: open result is 15, (OK)
[    12.905] ukiOpenByBusid: ukiOpenMinor returns 15
[    12.905] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.905] ukiOpenDevice: node name is /dev/ati/card1
[    12.905] ukiOpenDevice: open result is 15, (OK)
[    12.905] ukiOpenByBusid: ukiOpenMinor returns 15
[    12.905] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    12.905] ukiOpenDevice: node name is /dev/ati/card2
[    12.905] ukiOpenDevice: open result is 15, (OK)
[    12.905] ukiOpenByBusid: ukiOpenMinor returns 15
[    12.905] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    12.905] (II) fglrx(0): [uki] DRM interface version 1.0
[    12.905] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:3:0:0"
[    12.905] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    12.905] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f9f9a67a000
[    12.905] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    12.905] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    12.905] (II) fglrx(0): swlDriScreenInit done
[    12.905] (II) fglrx(0): Kernel Module Version Information:
[    12.905] (II) fglrx(0):     Name: fglrx
[    12.905] (II) fglrx(0):     Version: 13.25.5
[    12.905] (II) fglrx(0):     Date: Dec  6 2013
[    12.905] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    12.905] (II) fglrx(0): Kernel Module version matches driver.
[    12.905] (II) fglrx(0): Kernel Module Build Time Information:
[    12.905] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-52-generic
[    12.905] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    12.905] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    12.905] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    12.905] (II) fglrx(0): [uki] register handle = 0x00004000
[    12.969] (II) fglrx(0): Display width adjusted to to 1664 due to alignment constraints
[    12.969] (II) fglrx(0): DRI initialization successfull
[    12.996] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01110000
[    13.067] (==) fglrx(0): Backing store disabled
[    13.067] (II) Loading extension FGLRXEXTENSION
[    13.067] (**) fglrx(0): DPMS enabled
[    13.067] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.067] (**) fglrx(0): Textured Video is enabled.
[    13.067] (II) LoadModule: "glesx"
[    13.074] (II) Loading /usr/lib/xorg/modules/glesx.so
[    13.227] (II) Module glesx: vendor="X.Org Foundation"
[    13.227]     compiled for 1.4.99.906, module version = 1.0.0
[    13.227] (II) Loading extension GLESX
[    13.227] (II) fglrx(0): GLESX enableFlags = 592
[    13.236] (II) fglrx(0): GLESX is enabled
[    13.236] (II) LoadModule: "amdxmm"
[    13.236] (II) Loading /usr/lib/xorg/modules/amdxmm.so
[    13.251] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.251]     compiled for 1.4.99.906, module version = 2.0.0
[    13.270] (II) Loading extension AMDXVOPL
[    13.270] (II) Loading extension AMDXVBA
[    13.270] (II) fglrx(0): Enable composite support successfully
[    13.270] (WW) fglrx(0): Option "VendorName" is not used
[    13.270] (WW) fglrx(0): Option "ModelName" is not used
[    13.270] (II) fglrx(0): X context handle = 0x1
[    13.270] (II) fglrx(0): [DRI] installation complete
[    13.270] (==) fglrx(0): Silken mouse enabled
[    13.270] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.271] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.547] (--) RandR disabled
[    13.547] (II) fglrx(1): doing swlDriScreenInit
[    13.547] (II) fglrx(1): swlDriScreenInit for fglrx driver
[    13.547] ukiDynamicMajor: found major device number 250
[    13.547] ukiDynamicMajor: found major device number 250
[    13.547] ukiDynamicMajor: found major device number 250
[    13.547] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    13.547] ukiOpenDevice: node name is /dev/ati/card0
[    13.547] ukiOpenDevice: open result is 16, (OK)
[    13.547] ukiOpenByBusid: ukiOpenMinor returns 16
[    13.547] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.547] ukiOpenDevice: node name is /dev/ati/card1
[    13.547] ukiOpenDevice: open result is 16, (OK)
[    13.547] ukiOpenByBusid: ukiOpenMinor returns 16
[    13.547] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    13.547] (II) fglrx(1): [uki] DRM interface version 1.0
[    13.547] (II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    13.547] (II) fglrx(1): [uki] added 8192 byte SAREA at 0x18000
[    13.547] (II) fglrx(1): [uki] mapped SAREA 0x18000 to 0x7f9f9a481000
[    13.547] (II) fglrx(1): [uki] framebuffer handle = 0x19000
[    13.547] (II) fglrx(1): [uki] added 1 reserved context for kernel
[    13.547] (II) fglrx(1): swlDriScreenInit done
[    13.547] (II) fglrx(1): Kernel Module Version Information:
[    13.547] (II) fglrx(1):     Name: fglrx
[    13.547] (II) fglrx(1):     Version: 13.25.5
[    13.547] (II) fglrx(1):     Date: Dec  6 2013
[    13.547] (II) fglrx(1):     Desc: AMD FireGL DRM kernel module
[    13.547] (II) fglrx(1): Kernel Module version matches driver.
[    13.547] (II) fglrx(1): Kernel Module Build Time Information:
[    13.547] (II) fglrx(1):     Build-Kernel UTS_RELEASE:        3.2.0-52-generic
[    13.547] (II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
[    13.547] (II) fglrx(1):     Build-Kernel __SMP__:            yes
[    13.547] (II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
[    13.547] (II) fglrx(1): [uki] register handle = 0x0001a000
[    13.550] (II) fglrx(1): Display width adjusted to to 1664 due to alignment constraints
[    13.550] (II) fglrx(1): DRI initialization successfull
[    13.550] (II) fglrx(1): FBADPhys: 0xf400000000 FBMappedSize: 0x01110000
[    13.550] (==) fglrx(1): Backing store disabled
[    13.550] (**) fglrx(1): DPMS enabled
[    13.550] (**) fglrx(1): Textured Video is enabled.
[    13.550] (II) fglrx(1): GLESX enableFlags = 592
[    13.550] (II) fglrx(1): GLESX is enabled
[    13.570] (II) Loading extension AMDXVOPL
[    13.570] (II) Loading extension AMDXVBA
[    13.570] (II) fglrx(1): Enable composite support successfully
[    13.570] (WW) fglrx(1): Option "VendorName" is not used
[    13.570] (WW) fglrx(1): Option "ModelName" is not used
[    13.570] (II) fglrx(1): X context handle = 0x1
[    13.570] (II) fglrx(1): [DRI] installation complete
[    13.570] (==) fglrx(1): Silken mouse enabled
[    13.570] (==) fglrx(1): Using HW cursor of display infrastructure!
[    13.570] (II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.788] (--) RandR disabled
[    13.788] (II) fglrx(2): doing swlDriScreenInit
[    13.788] (II) fglrx(2): swlDriScreenInit for fglrx driver
[    13.788] ukiDynamicMajor: found major device number 250
[    13.788] ukiDynamicMajor: found major device number 250
[    13.788] ukiDynamicMajor: found major device number 250
[    13.788] ukiOpenByBusid: Searching for BusID PCI:5:0:0
[    13.788] ukiOpenDevice: node name is /dev/ati/card0
[    13.788] ukiOpenDevice: open result is 17, (OK)
[    13.788] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.788] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.788] ukiOpenDevice: node name is /dev/ati/card1
[    13.788] ukiOpenDevice: open result is 17, (OK)
[    13.788] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.788] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    13.788] ukiOpenDevice: node name is /dev/ati/card2
[    13.788] ukiOpenDevice: open result is 17, (OK)
[    13.788] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.788] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    13.788] ukiOpenDevice: node name is /dev/ati/card3
[    13.788] ukiOpenDevice: open result is 17, (OK)
[    13.788] ukiOpenByBusid: ukiOpenMinor returns 17
[    13.788] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    13.788] (II) fglrx(2): [uki] DRM interface version 1.0
[    13.788] (II) fglrx(2): [uki] created "fglrx" driver at busid "PCI:5:0:0"
[    13.788] (II) fglrx(2): [uki] added 8192 byte SAREA at 0x2e000
[    13.788] (II) fglrx(2): [uki] mapped SAREA 0x2e000 to 0x7f9f91c97000
[    13.788] (II) fglrx(2): [uki] framebuffer handle = 0x2f000
[    13.788] (II) fglrx(2): [uki] added 1 reserved context for kernel
[    13.788] (II) fglrx(2): swlDriScreenInit done
[    13.788] (II) fglrx(2): Kernel Module Version Information:
[    13.788] (II) fglrx(2):     Name: fglrx
[    13.788] (II) fglrx(2):     Version: 13.25.5
[    13.788] (II) fglrx(2):     Date: Dec  6 2013
[    13.788] (II) fglrx(2):     Desc: AMD FireGL DRM kernel module
[    13.788] (II) fglrx(2): Kernel Module version matches driver.
[    13.788] (II) fglrx(2): Kernel Module Build Time Information:
[    13.788] (II) fglrx(2):     Build-Kernel UTS_RELEASE:        3.2.0-52-generic
[    13.788] (II) fglrx(2):     Build-Kernel MODVERSIONS:        yes
[    13.788] (II) fglrx(2):     Build-Kernel __SMP__:            yes
[    13.788] (II) fglrx(2):     Build-Kernel PAGE_SIZE:          0x1000
[    13.788] (II) fglrx(2): [uki] register handle = 0x00030000
[    13.792] (II) fglrx(2): Display width adjusted to to 1664 due to alignment constraints
[    13.792] (II) fglrx(2): DRI initialization successfull
[    13.792] (II) fglrx(2): FBADPhys: 0xf400000000 FBMappedSize: 0x01110000
[    13.792] (==) fglrx(2): Backing store disabled
[    13.792] (**) fglrx(2): DPMS enabled
[    13.792] (**) fglrx(2): Textured Video is enabled.
[    13.792] (II) fglrx(2): GLESX enableFlags = 592
[    13.792] (II) fglrx(2): GLESX is enabled
[    13.815] (II) Loading extension AMDXVOPL
[    13.815] (II) Loading extension AMDXVBA
[    13.815] (II) fglrx(2): Enable composite support successfully
[    13.815] (WW) fglrx(2): Option "VendorName" is not used
[    13.815] (WW) fglrx(2): Option "ModelName" is not used
[    13.815] (II) fglrx(2): X context handle = 0x1
[    13.815] (II) fglrx(2): [DRI] installation complete
[    13.815] (==) fglrx(2): Silken mouse enabled
[    13.815] (==) fglrx(2): Using HW cursor of display infrastructure!
[    13.815] (II) fglrx(2): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    14.046] (--) RandR disabled
[    14.046] (II) fglrx(3): doing swlDriScreenInit
[    14.046] (II) fglrx(3): swlDriScreenInit for fglrx driver
[    14.047] ukiDynamicMajor: found major device number 250
[    14.047] ukiDynamicMajor: found major device number 250
[    14.047] ukiDynamicMajor: found major device number 250
[    14.047] ukiOpenByBusid: Searching for BusID PCI:6:0:0
[    14.047] ukiOpenDevice: node name is /dev/ati/card0
[    14.047] ukiOpenDevice: open result is 18, (OK)
[    14.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.047] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.047] ukiOpenDevice: node name is /dev/ati/card1
[    14.047] ukiOpenDevice: open result is 18, (OK)
[    14.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.047] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    14.047] ukiOpenDevice: node name is /dev/ati/card2
[    14.047] ukiOpenDevice: open result is 18, (OK)
[    14.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.047] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    14.047] ukiOpenDevice: node name is /dev/ati/card3
[    14.047] ukiOpenDevice: open result is 18, (OK)
[    14.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.047] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    14.047] ukiOpenDevice: node name is /dev/ati/card4
[    14.047] ukiOpenDevice: open result is 18, (OK)
[    14.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.047] ukiOpenByBusid: ukiGetBusid reports PCI:6:0:0
[    14.047] (II) fglrx(3): [uki] DRM interface version 1.0
[    14.047] (II) fglrx(3): [uki] created "fglrx" driver at busid "PCI:6:0:0"
[    14.047] (II) fglrx(3): [uki] added 8192 byte SAREA at 0x44000
[    14.047] (II) fglrx(3): [uki] mapped SAREA 0x44000 to 0x7f9f90450000
[    14.047] (II) fglrx(3): [uki] framebuffer handle = 0x45000
[    14.047] (II) fglrx(3): [uki] added 1 reserved context for kernel
[    14.047] (II) fglrx(3): swlDriScreenInit done
[    14.047] (II) fglrx(3): Kernel Module Version Information:
[    14.047] (II) fglrx(3):     Name: fglrx
[    14.047] (II) fglrx(3):     Version: 13.25.5
[    14.047] (II) fglrx(3):     Date: Dec  6 2013
[    14.047] (II) fglrx(3):     Desc: AMD FireGL DRM kernel module
[    14.047] (II) fglrx(3): Kernel Module version matches driver.
[    14.047] (II) fglrx(3): Kernel Module Build Time Information:
[    14.047] (II) fglrx(3):     Build-Kernel UTS_RELEASE:        3.2.0-52-generic
[    14.047] (II) fglrx(3):     Build-Kernel MODVERSIONS:        yes
[    14.047] (II) fglrx(3):     Build-Kernel __SMP__:            yes
[    14.047] (II) fglrx(3):     Build-Kernel PAGE_SIZE:          0x1000
[    14.047] (II) fglrx(3): [uki] register handle = 0x00046000
[    14.050] (II) fglrx(3): Display width adjusted to to 1664 due to alignment constraints
[    14.050] (II) fglrx(3): DRI initialization successfull
[    14.050] (II) fglrx(3): FBADPhys: 0xf400000000 FBMappedSize: 0x01110000
[    14.050] (==) fglrx(3): Backing store disabled
[    14.050] (**) fglrx(3): DPMS enabled
[    14.050] (**) fglrx(3): Textured Video is enabled.
[    14.050] (II) fglrx(3): GLESX enableFlags = 592
[    14.050] (II) fglrx(3): GLESX is enabled
[    14.072] (II) Loading extension AMDXVOPL
[    14.072] (II) Loading extension AMDXVBA
[    14.072] (II) fglrx(3): Enable composite support successfully
[    14.072] (WW) fglrx(3): Option "VendorName" is not used
[    14.072] (WW) fglrx(3): Option "ModelName" is not used
[    14.072] (II) fglrx(3): X context handle = 0x1
[    14.072] (II) fglrx(3): [DRI] installation complete
[    14.072] (==) fglrx(3): Silken mouse enabled
[    14.073] (==) fglrx(3): Using HW cursor of display infrastructure!
[    14.073] (II) fglrx(3): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    14.307] (--) RandR disabled
[    14.307] (II) fglrx(4): doing swlDriScreenInit
[    14.307] (II) fglrx(4): swlDriScreenInit for fglrx driver
[    14.307] ukiDynamicMajor: found major device number 250
[    14.307] ukiDynamicMajor: found major device number 250
[    14.307] ukiDynamicMajor: found major device number 250
[    14.307] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.307] ukiOpenDevice: node name is /dev/ati/card0
[    14.307] ukiOpenDevice: open result is 19, (OK)
[    14.307] ukiOpenByBusid: ukiOpenMinor returns 19
[    14.307] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.308] (II) fglrx(4): [uki] DRM interface version 1.0
[    14.308] (II) fglrx(4): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    14.308] (II) fglrx(4): [uki] added 8192 byte SAREA at 0x5a000
[    14.308] (II) fglrx(4): [uki] mapped SAREA 0x5a000 to 0x7f9f8ec09000
[    14.308] (II) fglrx(4): [uki] framebuffer handle = 0x5b000
[    14.308] (II) fglrx(4): [uki] added 1 reserved context for kernel
[    14.308] (II) fglrx(4): swlDriScreenInit done
[    14.308] (II) fglrx(4): Kernel Module Version Information:
[    14.308] (II) fglrx(4):     Name: fglrx
[    14.308] (II) fglrx(4):     Version: 13.25.5
[    14.308] (II) fglrx(4):     Date: Dec  6 2013
[    14.308] (II) fglrx(4):     Desc: AMD FireGL DRM kernel module
[    14.308] (II) fglrx(4): Kernel Module version matches driver.
[    14.308] (II) fglrx(4): Kernel Module Build Time Information:
[    14.308] (II) fglrx(4):     Build-Kernel UTS_RELEASE:        3.2.0-52-generic
[    14.308] (II) fglrx(4):     Build-Kernel MODVERSIONS:        yes
[    14.308] (II) fglrx(4):     Build-Kernel __SMP__:            yes
[    14.308] (II) fglrx(4):     Build-Kernel PAGE_SIZE:          0x1000
[    14.308] (II) fglrx(4): [uki] register handle = 0x0005c000
[    14.311] (II) fglrx(4): Display width adjusted to to 1664 due to alignment constraints
[    14.311] (II) fglrx(4): DRI initialization successfull
[    14.311] (II) fglrx(4): FBADPhys: 0xf400000000 FBMappedSize: 0x01110000
[    14.311] (==) fglrx(4): Backing store disabled
[    14.311] (**) fglrx(4): DPMS enabled
[    14.311] (**) fglrx(4): Textured Video is enabled.
[    14.311] (II) fglrx(4): GLESX enableFlags = 592
[    14.311] (II) fglrx(4): GLESX is enabled
[    14.329] (II) Loading extension AMDXVOPL
[    14.329] (II) Loading extension AMDXVBA
[    14.329] (II) fglrx(4): Enable composite support successfully
[    14.329] (WW) fglrx(4): Option "VendorName" is not used
[    14.329] (WW) fglrx(4): Option "ModelName" is not used
[    14.329] (II) fglrx(4): X context handle = 0x1
[    14.329] (II) fglrx(4): [DRI] installation complete
[    14.329] (==) fglrx(4): Silken mouse enabled
[    14.330] (==) fglrx(4): Using HW cursor of display infrastructure!
[    14.330] (II) fglrx(4): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    14.542] (--) RandR disabled
[    14.542] (II) Initializing built-in extension Generic Event Extension
[    14.542] (II) Initializing built-in extension SHAPE
[    14.542] (II) Initializing built-in extension MIT-SHM
[    14.542] (II) Initializing built-in extension XInputExtension
[    14.542] (II) Initializing built-in extension XTEST
[    14.542] (II) Initializing built-in extension BIG-REQUESTS
[    14.542] (II) Initializing built-in extension SYNC
[    14.542] (II) Initializing built-in extension XKEYBOARD
[    14.542] (II) Initializing built-in extension XC-MISC
[    14.542] (II) Initializing built-in extension SECURITY
[    14.542] (II) Initializing built-in extension XINERAMA
[    14.542] (II) Initializing built-in extension XFIXES
[    14.542] (II) Initializing built-in extension RENDER
[    14.542] (II) Initializing built-in extension RANDR
[    14.542] (II) Initializing built-in extension COMPOSITE
[    14.542] (II) Initializing built-in extension DAMAGE
[    14.543] ukiDynamicMajor: found major device number 250
[    14.543] ukiDynamicMajor: found major device number 250
[    14.543] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[    14.543] ukiOpenDevice: node name is /dev/ati/card0
[    14.543] ukiOpenDevice: open result is 20, (OK)
[    14.543] ukiOpenByBusid: ukiOpenMinor returns 20
[    14.543] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.543] ukiOpenDevice: node name is /dev/ati/card1
[    14.543] ukiOpenDevice: open result is 20, (OK)
[    14.543] ukiOpenByBusid: ukiOpenMinor returns 20
[    14.543] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    14.543] ukiOpenDevice: node name is /dev/ati/card2
[    14.543] ukiOpenDevice: open result is 20, (OK)
[    14.543] ukiOpenByBusid: ukiOpenMinor returns 20
[    14.543] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    14.959] ukiDynamicMajor: found major device number 250
[    14.959] ukiDynamicMajor: found major device number 250
[    14.959] ukiDynamicMajor: found major device number 250
[    14.959] ukiOpenDevice: node name is /dev/ati/card0
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiGetBusid returned 'PCI:1:0:0'
[    14.959] ukiOpenDevice: node name is /dev/ati/card1
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiGetBusid returned 'PCI:2:0:0'
[    14.959] ukiOpenDevice: node name is /dev/ati/card2
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiGetBusid returned 'PCI:3:0:0'
[    14.959] ukiOpenDevice: node name is /dev/ati/card3
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiGetBusid returned 'PCI:5:0:0'
[    14.959] ukiOpenDevice: node name is /dev/ati/card4
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiGetBusid returned 'PCI:6:0:0'
[    14.959] ukiOpenDevice: node name is /dev/ati/card5
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card6
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card7
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card8
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card9
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card10
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card11
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card12
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card13
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card14
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiOpenDevice: node name is /dev/ati/card15
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: open result is -1, (No such device)
[    14.959] ukiOpenDevice: Open failed
[    14.959] ukiDynamicMajor: found major device number 250
[    14.959] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.959] ukiOpenDevice: node name is /dev/ati/card0
[    14.959] ukiOpenDevice: open result is 21, (OK)
[    14.959] ukiOpenByBusid: ukiOpenMinor returns 21
[    14.959] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.853] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    15.854] ukiDynamicMajor: found major device number 250
[    15.854] ukiDynamicMajor: found major device number 250
[    15.854] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    15.854] ukiOpenDevice: node name is /dev/ati/card0
[    15.854] ukiOpenDevice: open result is 22, (OK)
[    15.854] ukiOpenByBusid: ukiOpenMinor returns 22
[    15.854] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.854] ukiOpenDevice: node name is /dev/ati/card1
[    15.854] ukiOpenDevice: open result is 22, (OK)
[    15.854] ukiOpenByBusid: ukiOpenMinor returns 22
[    15.854] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.858] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 1
[    15.858] ukiDynamicMajor: found major device number 250
[    15.858] ukiDynamicMajor: found major device number 250
[    15.858] ukiOpenByBusid: Searching for BusID PCI:5:0:0
[    15.858] ukiOpenDevice: node name is /dev/ati/card0
[    15.858] ukiOpenDevice: open result is 23, (OK)
[    15.858] ukiOpenByBusid: ukiOpenMinor returns 23
[    15.858] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.858] ukiOpenDevice: node name is /dev/ati/card1
[    15.858] ukiOpenDevice: open result is 23, (OK)
[    15.858] ukiOpenByBusid: ukiOpenMinor returns 23
[    15.858] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.858] ukiOpenDevice: node name is /dev/ati/card2
[    15.858] ukiOpenDevice: open result is 23, (OK)
[    15.858] ukiOpenByBusid: ukiOpenMinor returns 23
[    15.858] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    15.858] ukiOpenDevice: node name is /dev/ati/card3
[    15.858] ukiOpenDevice: open result is 23, (OK)
[    15.858] ukiOpenByBusid: ukiOpenMinor returns 23
[    15.858] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    15.862] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 2
[    15.862] ukiDynamicMajor: found major device number 250
[    15.862] ukiDynamicMajor: found major device number 250
[    15.862] ukiOpenByBusid: Searching for BusID PCI:6:0:0
[    15.862] ukiOpenDevice: node name is /dev/ati/card0
[    15.862] ukiOpenDevice: open result is 24, (OK)
[    15.862] ukiOpenByBusid: ukiOpenMinor returns 24
[    15.862] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.862] ukiOpenDevice: node name is /dev/ati/card1
[    15.862] ukiOpenDevice: open result is 24, (OK)
[    15.862] ukiOpenByBusid: ukiOpenMinor returns 24
[    15.862] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.862] ukiOpenDevice: node name is /dev/ati/card2
[    15.862] ukiOpenDevice: open result is 24, (OK)
[    15.862] ukiOpenByBusid: ukiOpenMinor returns 24
[    15.862] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    15.862] ukiOpenDevice: node name is /dev/ati/card3
[    15.862] ukiOpenDevice: open result is 24, (OK)
[    15.862] ukiOpenByBusid: ukiOpenMinor returns 24
[    15.862] ukiOpenByBusid: ukiGetBusid reports PCI:5:0:0
[    15.862] ukiOpenDevice: node name is /dev/ati/card4
[    15.862] ukiOpenDevice: open result is 24, (OK)
[    15.862] ukiOpenByBusid: ukiOpenMinor returns 24
[    15.862] ukiOpenByBusid: ukiGetBusid reports PCI:6:0:0
[    15.867] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 3
[    15.867] ukiDynamicMajor: found major device number 250
[    15.867] ukiDynamicMajor: found major device number 250
[    15.867] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.867] ukiOpenDevice: node name is /dev/ati/card0
[    15.867] ukiOpenDevice: open result is 25, (OK)
[    15.867] ukiOpenByBusid: ukiOpenMinor returns 25
[    15.867] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.871] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 4
[    15.872] ukiDynamicMajor: found major device number 250
[    15.872] ukiDynamicMajor: found major device number 250
[    15.872] ukiDynamicMajor: found major device number 250
[    15.872] ukiOpenDevice: node name is /dev/ati/card0
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiGetBusid returned 'PCI:1:0:0'
[    15.872] ukiOpenDevice: node name is /dev/ati/card1
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiGetBusid returned 'PCI:2:0:0'
[    15.872] ukiOpenDevice: node name is /dev/ati/card2
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiGetBusid returned 'PCI:3:0:0'
[    15.872] ukiOpenDevice: node name is /dev/ati/card3
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiGetBusid returned 'PCI:5:0:0'
[    15.872] ukiOpenDevice: node name is /dev/ati/card4
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiGetBusid returned 'PCI:6:0:0'
[    15.872] ukiOpenDevice: node name is /dev/ati/card5
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card6
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card7
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card8
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card9
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card10
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card11
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card12
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card13
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card14
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiOpenDevice: node name is /dev/ati/card15
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: open result is -1, (No such device)
[    15.872] ukiOpenDevice: Open failed
[    15.872] ukiDynamicMajor: found major device number 250
[    15.872] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.872] ukiOpenDevice: node name is /dev/ati/card0
[    15.872] ukiOpenDevice: open result is 26, (OK)
[    15.872] ukiOpenByBusid: ukiOpenMinor returns 26
[    15.872] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.437] (II) fglrx(0): OverDrive5 Detected!
[    16.443] (II) fglrx(0): Setting screen physical size to 423 x 317
[    16.443] (II) fglrx(0): OverDrive5 Detected!
[    16.446] (II) fglrx(1): Setting screen physical size to 423 x 317
[    16.446] (II) fglrx(0): OverDrive5 Detected!
[    16.450] (II) fglrx(2): Setting screen physical size to 423 x 317
[    16.450] (II) fglrx(0): OverDrive5 Detected!
[    16.454] (II) fglrx(3): Setting screen physical size to 423 x 317
[    16.454] (II) fglrx(0): OverDrive5 Detected!
[    16.457] (II) fglrx(4): Setting screen physical size to 423 x 317
[    16.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.602] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.602] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.602] (II) LoadModule: "evdev"
[    16.602] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.636] (II) Module evdev: vendor="X.Org Foundation"
[    16.636]     compiled for 1.11.3, module version = 2.7.0
[    16.636]     Module class: X.Org XInput Driver
[    16.636]     ABI class: X.Org XInput driver, version 16.0
[    16.636] (II) Using input driver 'evdev' for 'Power Button'
[    16.636] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.636] (**) Power Button: always reports core events
[    16.636] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.636] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.636] (--) evdev: Power Button: Found keys
[    16.636] (II) evdev: Power Button: Configuring as keyboard
[    16.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.636] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.636] (**) Option "xkb_rules" "evdev"
[    16.636] (**) Option "xkb_model" "pc105"
[    16.636] (**) Option "xkb_layout" "us"
[    16.637] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.637] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.637] (II) Using input driver 'evdev' for 'Power Button'
[    16.637] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.637] (**) Power Button: always reports core events
[    16.637] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.637] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.637] (--) evdev: Power Button: Found keys
[    16.637] (II) evdev: Power Button: Configuring as keyboard
[    16.637] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    16.637] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    16.637] (**) Option "xkb_rules" "evdev"
[    16.637] (**) Option "xkb_model" "pc105"
[    16.637] (**) Option "xkb_layout" "us"
[    16.637] (II) config/udev: Adding input device 2.4G RF Keyboard & Mouse (/dev/input/event2)
[    16.637] (**) 2.4G RF Keyboard & Mouse: Applying InputClass "evdev keyboard catchall"
[    16.637] (II) Using input driver 'evdev' for '2.4G RF Keyboard & Mouse'
[    16.637] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.637] (**) 2.4G RF Keyboard & Mouse: always reports core events
[    16.637] (**) evdev: 2.4G RF Keyboard & Mouse: Device: "/dev/input/event2"
[    16.637] (--) evdev: 2.4G RF Keyboard & Mouse: Vendor 0x4f3 Product 0x1a4
[    16.637] (--) evdev: 2.4G RF Keyboard & Mouse: Found keys
[    16.637] (II) evdev: 2.4G RF Keyboard & Mouse: Configuring as keyboard
[    16.637] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input2/event2"
[    16.637] (II) XINPUT: Adding extended input device "2.4G RF Keyboard & Mouse" (type: KEYBOARD, id 8)
[    16.637] (**) Option "xkb_rules" "evdev"
[    16.637] (**) Option "xkb_model" "pc105"
[    16.637] (**) Option "xkb_layout" "us"
[    16.637] (II) config/udev: Adding input device 2.4G RF Keyboard & Mouse (/dev/input/event3)
[    16.637] (**) 2.4G RF Keyboard & Mouse: Applying InputClass "evdev pointer catchall"
[    16.637] (**) 2.4G RF Keyboard & Mouse: Applying InputClass "evdev keyboard catchall"
[    16.637] (II) Using input driver 'evdev' for '2.4G RF Keyboard & Mouse'
[    16.637] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.637] (**) 2.4G RF Keyboard & Mouse: always reports core events
[    16.637] (**) evdev: 2.4G RF Keyboard & Mouse: Device: "/dev/input/event3"
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Vendor 0x4f3 Product 0x1a4
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found 9 mouse buttons
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found scroll wheel(s)
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found relative axes
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found x and y relative axes
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found absolute axes
[    16.638] (II) evdev: 2.4G RF Keyboard & Mouse: Forcing absolute x/y axes to exist.
[    16.638] (--) evdev: 2.4G RF Keyboard & Mouse: Found keys
[    16.638] (II) evdev: 2.4G RF Keyboard & Mouse: Configuring as mouse
[    16.638] (II) evdev: 2.4G RF Keyboard & Mouse: Configuring as keyboard
[    16.638] (II) evdev: 2.4G RF Keyboard & Mouse: Adding scrollwheel support
[    16.638] (**) evdev: 2.4G RF Keyboard & Mouse: YAxisMapping: buttons 4 and 5
[    16.638] (**) evdev: 2.4G RF Keyboard & Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.638] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input3/event3"
[    16.638] (II) XINPUT: Adding extended input device "2.4G RF Keyboard & Mouse" (type: KEYBOARD, id 9)
[    16.638] (**) Option "xkb_rules" "evdev"
[    16.638] (**) Option "xkb_model" "pc105"
[    16.638] (**) Option "xkb_layout" "us"
[    16.638] (II) evdev: 2.4G RF Keyboard & Mouse: initialized for relative axes.
[    16.638] (WW) evdev: 2.4G RF Keyboard & Mouse: ignoring absolute axes.
[    16.638] (**) 2.4G RF Keyboard & Mouse: (accel) keeping acceleration scheme 1
[    16.638] (**) 2.4G RF Keyboard & Mouse: (accel) acceleration profile 0
[    16.638] (**) 2.4G RF Keyboard & Mouse: (accel) acceleration factor: 2.000
[    16.638] (**) 2.4G RF Keyboard & Mouse: (accel) acceleration threshold: 4
[    16.638] (II) config/udev: Adding input device 2.4G RF Keyboard & Mouse (/dev/input/mouse0)
[    16.638] (II) No input driver specified, ignoring this device.
[    16.638] (II) This device may have been added with another device file.
[    16.638] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event4)
[    16.638] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.638] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    16.638] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.638] (**) Logitech USB Keyboard: always reports core events
[    16.638] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event4"
[    16.638] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    16.638] (--) evdev: Logitech USB Keyboard: Found keys
[    16.638] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    16.638] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input4/event4"
[    16.638] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 10)
[    16.638] (**) Option "xkb_rules" "evdev"
[    16.638] (**) Option "xkb_model" "pc105"
[    16.638] (**) Option "xkb_layout" "us"
[    16.638] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    16.638] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.638] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    16.638] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.638] (**) Logitech USB Keyboard: always reports core events
[    16.638] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    16.638] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    16.638] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    16.639] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    16.639] (--) evdev: Logitech USB Keyboard: Found keys
[    16.639] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    16.639] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    16.639] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input5/event5"
[    16.639] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 11)
[    16.639] (**) Option "xkb_rules" "evdev"
[    16.639] (**) Option "xkb_model" "pc105"
[    16.639] (**) Option "xkb_layout" "us"
[    16.639] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    16.639] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    16.639] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    16.639] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    16.639] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    16.647] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    16.746] (II) fglrx(0): Framebuffer compression enabled from crtc[0]: mcAddr=0xf40b900000 with=0xa00 height=0x1934
[    16.752] (II) fglrx(1): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    16.852] (II) fglrx(0): Framebuffer compression enabled from crtc[0]: mcAddr=0xf40b900000 with=0xa00 height=0x1934
[    16.861] (II) fglrx(2): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.055] (II) fglrx(0): Framebuffer compression enabled from crtc[0]: mcAddr=0xf40b900000 with=0xa00 height=0x1934
[    17.067] (II) fglrx(3): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.262] (II) fglrx(0): Framebuffer compression enabled from crtc[0]: mcAddr=0xf40b900000 with=0xa00 height=0x1934
[    17.262] (II) fglrx(4): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.318] (II) fglrx(0): Framebuffer compression enabled from crtc[0]: mcAddr=0xf40b900000 with=0xa00 height=0x1934
[    19.750] (II) fglrx(0): Cannot get EDID information for CRT1
[    19.784] (II) fglrx(0): Cannot get EDID information for CRT1 [COLOR=#000000][    22.384] (II) fglrx(0): Cannot get EDID information for CRT1[/COLOR]
```

---

