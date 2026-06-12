---
title: "Network and sound devices suddenly not found."
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by 16777216 on 2009-02-14
I turned on my computer this morning and found that my sound and ethernet could not be found.

one of the ethernet devices and the sound is build in to the motherboard the other ethernet card is an add-on card.

I do not remember changing any settings nor do I remember installing or updating any software since the last reboot.

The live CD works fine so I do not believe this is a hardware problem.

lspci shows the sound and both network devices.
The system logs show no problems.
I can't understand what is going on.

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] #00 [00fe]
    Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device 0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20)
    Subsystem: Biostar Microtech Int'l Corp Device 3402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f565:3402
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f400 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5401
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
    Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: fdb00000-fdbfffff
    Capabilities: [b8] Subsystem: Gammagraphx, Inc. Device 0000
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 8213
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 2501
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d400 [size=8]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=512M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at fb000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel modules: nvidiafb

04:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at cc00 [size=256]
    Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too
```

---

### Post by cariboo on 2009-02-14
Could you post the out put of the following commands:

```
sudo lshw -C network
```

```
sudo lshw -C bridge
```

```
sudo lshw -C multimedia
```

These commands will tell us the details of the devices and whether there are drivers loaded. I have a motherboard with the same chipset and the onbaord nic shows up as a bridge device.

Jim

---

### Post by 16777216 on 2009-02-14
Never mind I just said the h*** with it and reinstalled.

---

