---
title: "Wireless not working"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by surfsupfriends on 2009-10-27
I have dual boot Ubuntu/Vista - the wireless works fine in Vista but with Ubuntu it'll detect and connect to the network but not let me browse on firefox/any other application using an internet connection. I'm using a wired connection at the moment and it works fine. I'm a total noob with linux, but i looked on some other threads to find a solution but to no avail, do i need to d/l a new driver for the wireless?

Here's the wireless chipset on my pc:

[INDENT]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, fast devsel, latency 0, IRQ 2296
    Memory at f2400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, fast devsel, latency 0
    Memory at f2100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2804800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f4000000-f5ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 88000000-880fffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f20fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2804c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2298
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f2804000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: medium devsel, IRQ 10
    Memory at 88100000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Fujitsu Siemens Computers Device 1160
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    I/O ports at 3000 [size=256]
    Memory at f2010000 (64-bit, prefetchable) [size=4K]
    Memory at f2000000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f2020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
[/INDENT]

---

### Post by Iowan on 2009-10-27
When it detects/connects, check **ifconfig -a** for IP address. Can you **ping** the router from the machine? Can you **ping** internet by name or address? (Success via address, but not name suggests DNS issue.)

---

