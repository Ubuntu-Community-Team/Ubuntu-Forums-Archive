---
title: "ubuntu 8.10 sound recorder not working"
date: 2008-10-21
forum: Multimedia Software
---

### Post by shafi on 2008-10-21
Hi folks,
I have tried to record sound in ubuntu 8.10 but it's not working, also I can not do skype calls in my laptop, I have a COMPAQ presario C700.
I have followed the guide line of the skype regarding the sound problem but doesn't worked for me, this is the link:
[http://forum.skype.com/index.php?showtopic=194741]("http://forum.skype.com/index.php?showtopic=194741")
can anyone help me regarding this issue?
thi is the out put of lspci command:
[HTML]
sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 30d0 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, fast devsel, latency 0
	Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Device 5051
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 91300000-923fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30d9
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 92404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 91200000-912fffff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 30d9

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30a0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 222
	I/O ports at 30b8 [size=8]
	I/O ports at 30dc [size=4]
	I/O ports at 30b0 [size=8]
	I/O ports at 30d8 [size=4]
	I/O ports at 3020 [size=32]
	Memory at 92404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: medium devsel, IRQ 11
	Memory at 92404c00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Kernel driver in use: ndiswrapper
	Kernel modules: ath_pci

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 30d9
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at 1000 [size=256]
	Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp


[/HTML]

---

### Post by shafi on 2008-10-22
any idea?

---

