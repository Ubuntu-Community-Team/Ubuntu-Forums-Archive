---
title: "headset not working"
date: 2010-12-28
forum: Multimedia Software
---

### Post by yeklef on 2010-12-28
Edit: in case anyone looks several pages into the forum, this one is solved

I have been trying to get my new headset to work in Ubuntu 10.10.  It is a Dynex DX-840.  It connects via usb.  I ran lsusb and it shows up there as follows.

[PHP]:~$ lsusb
Bus 002 Device 008: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
... (other attached usb devices)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]Since I know that my computer sees the headset(from the lsusb command, and the fact that when I plug the headset in, it makes a sound in the headset, although I guess that could just be because they are getting power), I did a number of the things from this thread [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , but it quickly went over my head.  Following are some of the results though, in case they are useful.  (I do have speakers attached to an internal sound card as well, so they are probably affecting the results.)  

Thanks for any help

[PHP]:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1[/PHP][PHP]:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fd700000-fd7fffff
    Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fd900000-fd9fffff
    Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 60000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: fda00000-fdafffff
    Capabilities: <access denied>

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d400 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

04:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Device 2000
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at fdbf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at cc00 [size=8]
    Capabilities: <access denied>

charlie@Geronimo:~$ lsusb
Bus 002 Device 008: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
charlie@Geronimo:~$ ^C
charlie@Geronimo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
charlie@Geronimo:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fd700000-fd7fffff
    Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fd900000-fd9fffff
    Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 60000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: fda00000-fdafffff
    Capabilities: <access denied>

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d400 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

04:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Device 2000
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at fdbf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at cc00 [size=8]
    Capabilities: <access denied>[/PHP]

---

