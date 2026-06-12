---
title: "Intermitting problems with connection to wireless networks"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by VidJa on 2010-01-14
Hi all,

I have some problems with connecting to my wireless network (WPA2 security) on Ubuntu 9.10 64 bit.

Upon boot I can sometimes connect and sometime it takes minutes or more to ask for my wireless key to connect. When I give my key, nm-applet keeps spinning until it asks for the password again etc.) At random it connects and disconnects from the AP (sitting at about 5m) 
At times I can get stable connections, but still disconnects at random. On the same computer I also run Windows 7 (Vista before) with always instant connection. My Faithful Powerbook also always connects instantly.

The problem above also appears in Live-CD mode or with Knoppix 6.2

Does anyone experience this behavious as well?
I have a Dell 630c with an Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61).
The AP is a Linksys  WAG54G






00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Device 0232
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
	Subsystem: Dell Device 0232
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febd96f0 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: heci
	Kernel modules: heci

00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Device 0232
	Flags: 66MHz, fast devsel, IRQ 18
	I/O ports at ef88 [size=8]
	I/O ports at ef80 [size=4]
	I/O ports at ef90 [size=8]
	I/O ports at ef84 [size=4]
	I/O ports at efa0 [size=16]
	Capabilities: <access denied>

00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c) (prog-if 02)
	Subsystem: Dell Device 0232
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ef98 [size=8]
	Memory at febda000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
	Subsystem: Dell Device 0232
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at febdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at efe0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f20 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at febdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f9e00000-f9efffff
	Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Dell Device 01f9
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at febd9800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Dell Device 01f9
	Flags: medium devsel, IRQ 5
	Memory at febd9700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
	Subsystem: Dell Device 01f9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
	Subsystem: Dell Device 0232
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 19
	Memory at f9e00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 84000000-87fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10)
	Subsystem: Dell Device 0232
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f9eff000 (32-bit, non-prefetchable) [size=4K]
	Memory at f9efe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1121
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f9ffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

---

### Post by FrodeA on 2010-01-14
I've got the same problem after upgrading to 9.10 64-bit. Use a Compal custombuilt laptop with same mainboard and wifi-card from intel. Use a .11n-network with WPA2-encryption.

When firing up my machine, connecting to the wireless network can take from 10 sec to 6 minutes. If it takes too long, clicking on networkmanager icon in notification area shows the correct network and correct information, but "connect" button greyed out. Easiest option (in the short run...) is to type in the network name and key to log on. I've not been able to find out what is wrong, though... :(

Hope someone on these forums can help?

---

