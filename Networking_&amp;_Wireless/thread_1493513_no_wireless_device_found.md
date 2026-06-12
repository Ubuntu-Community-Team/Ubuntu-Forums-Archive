---
title: "no wireless device found"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by Raffihsieh on 2010-05-25
I just recently put ubuntu onto my netbook, but i am having problems getting the wireless to work.

i have an Asus Eee pc 1000He and i'm running ubuntu 10.04 right now.

i have no clue what to do... somebody please help?

here's some stuff that might help?
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8340
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8340
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8340
    Flags: bus master, fast devsel, latency 0
    Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 834a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f8000000-fbefffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 830f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=16]
    Memory at f7eb7800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 8324
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E
    Kernel modules: atl1e


does this bit at the end about the ethernet controller also mean that it detects wireless?
because otherwise i do not see any wireless device. but obviously my netbook has a wireless card

---

