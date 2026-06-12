---
title: "Sound problem in ubuntu for acer aspire g600"
date: 2009-05-13
forum: Multimedia Software
---

### Post by pulidilip on 2009-05-13
Hardware Information
--------------------

Motherboard          :  
System               :  Acer Aspire G600P
BIOS                 :  Phoenix 6.00 PG

Sound                : Avance AC97 Audio
Video                : SiS 650_651
 
I AM NEW TO UBUNTU NOW I AM USING **[Ubuntu 9.04 - Jaunty Jackalope]("http://www.ubuntu.com/getubuntu/download")** I AM NOT GETTING SOUND PLEASE HELP ME FRIENDS
I AM USING ACER ASPIRE G600

THANK YOU BYE

---

### Post by pulidilip on 2009-05-13
i tried a lot but not getting sound please say how to fix problem here i am giving my pc
information i am very new to linux please fix my problem

                                                           [COLOR=Red]FULL INFORMATION[/COLOR]

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
[-o<[-o<:cry:


Names of available sound cards:
SI7012
SAA7134
dilip@devaraju:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

                                        [COLOR=Red]lspci-v[/COLOR]
dilip@devaraju:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
    Subsystem: Silicon Integrated Systems [SiS] 651 Host
    Flags: bus master, medium devsel, latency 32
    Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
    Flags: bus master, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ec000000-ec0fffff
    Prefetchable memory behind bridge: e0000000-e7ffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
    Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
    Flags: medium devsel
    I/O ports at 10c0 [size=32]
    Kernel driver in use: sis96x_smbus
    Kernel modules: i2c-sis96x

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at ec120000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 128, IRQ 16
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 4000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at e400 [size=256]
    I/O ports at e800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0                                  [EMAIL="pulidilip@yahoo.co.in"]pulidilip@yahoo.co.in[/EMAIL]

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at ec121000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ec122000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at ec123000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: bus master, medium devsel, latency 32, IRQ 23
    Memory at ec124000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Innovative Integration Device 2001
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at ec125000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at ec00 [size=256]
    Memory at ec126000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 30020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
    Subsystem: Acer Incorporated [ALI] Device 0018
    Flags: 66MHz, medium devsel, IRQ 11
    BIST result: 00
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at ec000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at c000 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb
 
nothing works shall i disable bios sound auto please help me

---

