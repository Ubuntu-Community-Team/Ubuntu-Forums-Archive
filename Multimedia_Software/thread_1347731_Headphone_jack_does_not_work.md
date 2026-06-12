---
title: "Headphone jack does not work"
date: 2009-12-06
forum: Multimedia Software
---

### Post by 2quick on 2009-12-06
Hello!

I have installed Ubuntu 9.10(32-bit) on my laptop and for the most part everything is working fine.  My only current problem is the fact that my headphone jack does not work. I can get sound out of it if I pull the jack slightly out, but it is very touchy.  If this helps here is the bit of info about the computer:

```
laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And

```
philip@philip-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a3
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
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
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fdf00000-fdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe000000-fe9fffff
	Prefetchable memory behind bridge: 00000000f6000000-00000000f8efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=32]
	Memory at f9fff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GS] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 1992
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fd000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at fdffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 16d5
	Flags: bus master, fast devsel, latency 0, IRQ 30
	I/O ports at e800 [size=256]
	Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Memory at f8fe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

07:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at febff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 19a7
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at febfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f


```

Thank you sooo much for any help!

---

### Post by 2quick on 2009-12-09
Still trying to work it out...

---

