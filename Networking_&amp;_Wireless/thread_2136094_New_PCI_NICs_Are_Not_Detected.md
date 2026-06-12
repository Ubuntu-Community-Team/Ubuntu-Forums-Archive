---
title: "New PCI NICs Are Not Detected"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by hmac84 on 2013-04-16
**Problem:** No new pci devices are being detected. lspci does not show the devices. Devices in question are some intel NICs which are supported by the e1000 driver. It makes no difference which slot they are installed in. I cannot see any reference in the dmesg output to the devices.

**OS:** Ubuntu Server 12.04.2 LTS

**PCI Hardware: **
[LIST]
[*]1x Onboard Intel 82589LM Nic (functioning)
[*]1x Onboard Intel 82574L Nic (functioning)
[*]2x PCI-E Intel 82574L Nic (not detected)
[/LIST]
**Background:** This was a fully functioning server with the Intel NICs installed previously. Motherboard was replaced under warranty and the new onboard NICs messed up the /etc/udev/rules.d/70-persistent-net.rules presumably as ubuntu saw different MAC adresses and appended the new cards onto the end. To fix this I followed advice elsewhere to remove the entries in /etc/udev/rules.d/70-persistent-net.rules and reboot. Since the reboot only the onboard cards are being detected.

**lspci -v**
```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	Subsystem: Intel Corporation Device 2010
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 05)
	Subsystem: Intel Corporation Device 3578
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c2400000 (32-bit, non-prefetchable) [size=128K]
	Memory at c2470000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 4040 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at c2460000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c1900000-c22fffff
	Prefetchable memory behind bridge: 00000000c2500000-00000000c2efffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Intel Corporation Device 7270
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c2300000-c23fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Intel Corporation Device 7270
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: c0000000-c18fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Intel Corporation Device 7270
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 7270
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at c2450000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: [50] Subsystem: Intel Corporation Device 7270

00:1f.0 ISA bridge: Intel Corporation C204 Chipset Family LPC Controller (rev 05)
	Subsystem: Intel Corporation Device 7270
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 05)
	Subsystem: Intel Corporation Device 7270
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 4090 [size=8]
	I/O ports at 4080 [size=4]
	I/O ports at 4070 [size=8]
	I/O ports at 4060 [size=4]
	I/O ports at 4020 [size=32]
	Memory at c2440000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Intel Corporation Device 7270
	Flags: medium devsel, IRQ 5
	Memory at c2430000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
	Subsystem: Intel Corporation Device 3578
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c2300000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=32]
	Memory at c2320000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [a0] MSI-X: Enable+ Count=5 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-1e-67-ff-ff-79-cd-a4
	Kernel driver in use: e1000e
	Kernel modules: e1000e

03:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 0102
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c1810000 (32-bit, non-prefetchable) [size=16K]
	Memory at c1000000 (32-bit, non-prefetchable) [size=8M]
	Expansion ROM at c1800000 [disabled] [size=64K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [e4] Express Legacy Endpoint, MSI 00
	Capabilities: [54] MSI: Enable- Count=1/1 Maskable- 64bit-

```

Can anyone help with this?

Thanks

---

### Post by hmac84 on 2013-04-16
Turns out it was an odd Bios issue. Resetting bios to defaults allowed them to be detected again.

---

