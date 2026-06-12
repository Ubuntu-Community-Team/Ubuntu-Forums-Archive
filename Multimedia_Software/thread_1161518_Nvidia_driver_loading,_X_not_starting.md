---
title: "Nvidia driver loading, X not starting"
date: 2009-05-16
forum: Multimedia Software
---

### Post by Tony Richards on 2009-05-16
I'm having a difficult time getting X to run after installing an Nvidia driver.

I'm running Ubuntu 9.0.4 64 bit with a KFN32-D SLI motherboard, two Opteron processors, two Nvidia 8800 GTX video cards.

I upgraded from Windows XP.  I'm not sure if this has anything to do with it, but when I reformatted, the video cards were in SLI mode.  The video cards worked fine with Windows XP, so I'm sure I'm just doing something wrong with the driver installation or something.

I've tried all of the NVidia drivers.

X runs fine until I install any of the Nvidia drivers, at which point the computer will start, but X doesn't, and I'm left with just a console login.

I have no clue where to start.

lspci output:
```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0
    Kernel modules: ck804xrom

00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 2a00 [size=64]
    I/O ports at 2a80 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at ebebf000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at ebebec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd

00:05.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85)
    Subsystem: ASUSTeK Computer Inc. Device 823a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=8]
    I/O ports at b080 [size=4]
    I/O ports at b000 [size=16]
    Memory at ebebd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
    Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: sata_nv

00:05.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85)
    Subsystem: ASUSTeK Computer Inc. Device 823a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at ac00 [size=8]
    I/O ports at a880 [size=4]
    I/O ports at a800 [size=8]
    I/O ports at a480 [size=4]
    I/O ports at a400 [size=16]
    Memory at ebebc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
    Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: sata_nv

00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: ebf00000-ebffffff
    Capabilities: [b8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 8210
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [160] Advanced Error Reporting <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ec000000-efffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [160] Advanced Error Reporting <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface
    Capabilities: [a0] HyperTransport: Host or Secondary Interface
    Capabilities: [c0] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface
    Capabilities: [a0] HyperTransport: Host or Secondary Interface
    Capabilities: [c0] HyperTransport: Host or Secondary Interface

00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 815b
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at ebfff800 (32-bit, non-prefetchable) [size=2K]
    Memory at ebff8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
    Capabilities: [44] Express PCI/PCI-X Bridge, MSI 00
    Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] Power Management version 2
    Capabilities: [d8] PCI-X bridge device
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [300] Power Budgeting <?>
    Kernel modules: shpchp

04:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
    Subsystem: eVga.com. Corp. Device c831
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ef000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ec000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    Expansion ROM at eefe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

20:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

20:01.0 RAM memory: nVidia Corporation MCP55 LPC Bridge (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at cbdff000 (32-bit, non-prefetchable) [size=4K]
    Kernel modules: ck804xrom

20:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81f0
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at dc00 [size=64]
    I/O ports at d880 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

20:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=20, secondary=21, subordinate=21, sec-latency=0
    Memory behind bridge: cbe00000-cbefffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

20:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=20, secondary=22, subordinate=22, sec-latency=0
    Memory behind bridge: cbf00000-cbffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

20:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=20, secondary=23, subordinate=23, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: cc000000-cfffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

21:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8209
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    Memory at cbef0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Vital Product Data <?>
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [d0] Express Endpoint, MSI 00
    Kernel driver in use: tg3
    Kernel modules: tg3

22:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8209
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    Memory at cbff0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Vital Product Data <?>
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [d0] Express Endpoint, MSI 00
    Kernel driver in use: tg3
    Kernel modules: tg3

23:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
    Subsystem: eVga.com. Corp. Device c831
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at cf000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    Expansion ROM at cefe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

```Xorg.0.log:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Sullivan 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 16 18:33:43 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@4:0:0) nVidia Corporation G80 [GeForce 8800 GTX] rev 162, Mem @ 0xef000000/16777216, 0xd0000000/268435456, 0xec000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(--) PCI: (0@35:0:0) nVidia Corporation G80 [GeForce 8800 GTX] rev 162, Mem @ 0xcf000000/16777216, 0xb0000000/268435456, 0xcc000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [25] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [26] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [27] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [28] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [29] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [30] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [31] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [36] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [37] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [38] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [39] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [40] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [41] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [42] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [43] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [44] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [45] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [46] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [47] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Tue Mar 24 06:11:47 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Tue Mar 24 05:51:43 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: 
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```The nvidia kernel driver is loading correctly from what I can tell, but X isn't finding the device.

I've played around with SLI and non-SLI configurations, but no dice.  What are my options?

Any help would be appreciated.

Thanks

---

### Post by GeekGirl1 on 2009-05-17
Did you try installing the proprietary drivers mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=1161518](http://ubuntuforums.org/showthread.php?t=1161518) (nVidia latest Drivers - How to install - (180.xx - 185.xx) ) Post #1 has what you need.

I'm using a single GTX-280. Different problems. What worked for me was to remove NVidia's proprietary drivers and use the ubuntu drivers.

But first, can you get into Gnome using the fail-safe (recovery) mode? Hit ESC when booting and go into recovery mode. Select "xfix" from the choices and continue to boot. Can you get into Gnome? If so, use Synaptic Package Manager to uninstall (reboot) then reinstall the nvidia drivers. Search for "nvidia".

If you can't get into Gnome, then run the manual install procedure. Boot into recovery mode, then go into the "netroot" option. cd to the directory where the Nvidia driver is located and install it.

I just went through a number of driver installations / uninstalls and have everything working. (You may also need to install libgll1-mesa-glx to get glxgears working.)

Not much, but maybe something listed above will work.

---

