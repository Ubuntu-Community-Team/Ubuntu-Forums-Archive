---
title: "permisions all messed up"
date: 2012-08-19
forum: Multimedia Software
---

### Post by Dawnbandit on 2012-08-19
Hey, whenever I try to run all media files as non-root I get this error 
```
 [COLOR=#ff0000]Audio output failed:[/COLOR]
 [COLOR=#000000]The audio device "default" could not be used:[/COLOR]
 [COLOR=#000000]Permission denied.[/COLOR]
 
```I tried running ```
sudo adduser will audio_default
``` it ran fine but it still didn't fix the problem, i tried ```
lspci -v
``` and got this (I noticed the Capabilities: <access denied> which is weird) ```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0
    Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe000000 (32-bit, non-prefetchable) [size=128K]
    Memory at fe025000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T60
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fc000000-fdffffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: dc000000-df3fffff
    Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d8000000-d9ffffff
    Prefetchable memory behind bridge: 00000000dfb00000-00000000dfbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d4000000-d5ffffff
    Prefetchable memory behind bridge: 00000000df800000-00000000df8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d0000000-d1ffffff
    Prefetchable memory behind bridge: 00000000df500000-00000000df5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 18c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18e0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
    I/O behind bridge: 00007000-0000afff
    Memory behind bridge: f8300000-fbffffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
    Subsystem: Lenovo T61
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1c00 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
    I/O ports at 1c50 [size=8]
    I/O ports at 1c44 [size=4]
    I/O ports at 1c48 [size=8]
    I/O ports at 1c40 [size=4]
    I/O ports at 1c20 [size=32]
    Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: medium devsel, IRQ 11
    Memory at fe227400 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c60 [size=32]
    Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1010
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at df3fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwl4965
    Kernel modules: iwl4965

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Lenovo Device 20c6
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
    Memory window 0: f4000000-f7fff000 (prefetchable)
    Memory window 1: 80000000-83fff000
    I/O window 0: 00007400-000074ff
    I/O window 1: 00007000-000070ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 20c7
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

16:00.0 USB controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
    Subsystem: NEC Corporation Device 1735
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

16:00.1 USB controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
    Subsystem: NEC Corporation Device 1033
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at 80001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

16:00.2 USB controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Aten International Co. Ltd. Device 00e0
    Flags: bus master, medium devsel, latency 68, IRQ 16
    Memory at 80002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

```Can anyone please help.
Turns out I had to run  sudo chown -R will '/home/will/' to get permissions back.

---

