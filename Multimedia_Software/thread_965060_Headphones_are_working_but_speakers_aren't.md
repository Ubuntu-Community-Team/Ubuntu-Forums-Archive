---
title: "Headphones are working but speakers aren't"
date: 2008-10-31
forum: Multimedia Software
---

### Post by gusfm on 2008-10-31
Hello, I'm having some trouble with my laptop speakers sound. It used to work properly on hardy till september, then suddenly speakers stop working (probably after some kernel or alsa update). Now the problem continues with intrepid. The weird thing is that headphones are working fine.

```

$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fc200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fc486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fc489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fc487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fc489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:30d6
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd, ata_generic, pata_acpi

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=64
	Memory behind bridge: fc100000-fc1fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at fc484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci, ata_generic, pata_acpi

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
	Memory at fc488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at fc489c00 (32-bit, non-prefetchable) [size=256]
	Memory at fc489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-fbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	Memory behind bridge: fc000000-fc0fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at fc100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at fc100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at fc100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Hewlett-Packard Company Device 30d6
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at fc101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
	Subsystem: Hewlett-Packard Company Device 1374
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: ssb, wl
```


I tried compilling alsa, but it didn't worked (or at least I haven't done it wright).
I'm using 64 bit intrepid, although I was having the same problem with 32 bit hardy.
Oh, and my laptop is an HP dv2608ca.

Is anyone having the same problem?

Thanks.

---

### Post by gusfm on 2008-11-02
bump

---

