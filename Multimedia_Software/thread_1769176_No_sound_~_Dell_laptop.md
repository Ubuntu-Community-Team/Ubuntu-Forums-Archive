---
title: "No sound ~ Dell laptop"
date: 2011-05-27
forum: Multimedia Software
---

### Post by Iratezombiemann on 2011-05-27
I'm having problems with sound on my laptop, everything else runs fine.  I tried the comprehensive sound problems thread, but I only really get to step two or three before this happens:

sorin@sorin-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
sorin@sorin-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0
    Memory at fc400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fc900800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f6000000-f7ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f8000000-f9ffffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: fc500000-fc5fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fc900c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Memory behind bridge: fc600000-fc6fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Dell Device 02a0
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at fc900000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02a0
    Flags: medium devsel, IRQ 10
    Memory at c0200000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
    Subsystem: Dell Device 02a0
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at fc500000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at fc600000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fc600800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at fc600c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 02a0
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at fc601000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

sorin@sorin-laptop:~$ 


Can anyone help me?

---

### Post by Iratezombiemann on 2011-05-27
This might help some [http://www.alsa-project.org/db/?f=a03eb3a15e83ec083f57f54d025d5b6d0fb17dc4](http://www.alsa-project.org/db/?f=a03eb3a15e83ec083f57f54d025d5b6d0fb17dc4)

---

