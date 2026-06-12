---
title: "HP 530 wireless switch disabled"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by ianthealy on 2012-05-24
I have a fresh install of Ubuntu 12.04 (32 bit) on an HP 530 laptop. It has a physical button to turn on wireless networking, but the button is unresponsive and wireless remains disabled. The exact phrase in the Wireless Networking menu is "wireless is disabled by hardware switch".

I'm pretty sure I will get asked about lspci -v, so here it is to start:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0400000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 3000 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0480000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, fast devsel, latency 0
    Memory at f0500000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0580000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 7fa00000-7fbfffff
    Prefetchable memory behind bridge: 000000007fc00000-000000007fdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0000000-f00fffff
    Prefetchable memory behind bridge: 000000007f800000-000000007f9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 3020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at f0584000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0100000-f03fffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01) (prog-if 80 [Master])
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 3040 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, medium devsel, latency 168, IRQ 18
    Memory at f0100000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 84000000-87fff000
    I/O window 0: 00002800-000028ff
    I/O window 1: 00002400-000024ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
    Subsystem: Hewlett-Packard Company Device 30d5
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at f0101000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 2000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

```I'm looking for help in enabling the wireless without needing to use the button or else forcing it to respond. As always, your help is greatly appreciated!

---

### Post by ianthealy on 2012-05-25
I found a solution to this in AskUbuntu.

```
sudo rfkill unblock all
```

This enabled the wireless radio on the hardware switch and also in Network Connections. I'm marking this one as solved.

---

