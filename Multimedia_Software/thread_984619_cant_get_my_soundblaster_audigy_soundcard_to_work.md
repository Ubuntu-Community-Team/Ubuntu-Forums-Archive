---
title: "cant get my soundblaster audigy soundcard to work"
date: 2008-11-16
forum: Multimedia Software
---

### Post by ntense on 2008-11-16
i just did a fresh install of ubuntu studio 8.10 and i cant get my soundblaster sound card to work.
i tried using the sticky posted here to get it working: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

i make it as far as step 2 and it dosent show up

lspci -v command returns output of:```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Giga-byte Technology Device 2570
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fa000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: e8000000-f7ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 88000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device 24d1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at c000 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c800 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at d000 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: medium devsel, IRQ 9
	I/O ports at 1400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fa001000 (32-bit, non-prefetchable) [size=512]
	Memory at fa002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Linksys Device 0042
	Flags: bus master, fast devsel, latency 32, IRQ 21
	Memory at f9020000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at a000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: ATI Technologies Inc Device 2002
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at a400 [size=256]
	Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: ATI Technologies Inc Device 2003
	Flags: bus master, medium devsel, latency 32
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at f9010000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f9022000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a800 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

hac@cortana:~$ clear

hac@cortana:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Giga-byte Technology Device 2570
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fa000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: e8000000-f7ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 88000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device 24d1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at c000 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c800 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at d000 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 24d2
	Flags: medium devsel, IRQ 9
	I/O ports at 1400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fa001000 (32-bit, non-prefetchable) [size=512]
	Memory at fa002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Linksys Device 0042
	Flags: bus master, fast devsel, latency 32, IRQ 21
	Memory at f9020000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at a000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: ATI Technologies Inc Device 2002
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at a400 [size=256]
	Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: ATI Technologies Inc Device 2003
	Flags: bus master, medium devsel, latency 32
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at f9010000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f9022000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a800 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100
 

```

the onboard soundcard shows up but not my soundblaster. what could be the problem? any help would be greatly appreciated.. thank you in advance

---

