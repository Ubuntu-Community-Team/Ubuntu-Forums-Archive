---
title: "No System Sound Intel ALC260 analog device"
date: 2011-10-26
forum: Multimedia Software
---

### Post by novelty07 on 2011-10-26
Dear Doctor

have a bit of a bizzaro problem after installing Oneiric Ocelot. My system sound do not work. i.e.

No Drums on startup.
No pings or pongs.
Devices are not detected on system (sound settings, no hardware is shown) but aplay -1 shows the card.

So songs (mp3) & Video (avi) work well. However Banshee errors occur far too much. Mind I have been using the system for only a day.

Went through the guide and here are the o/ps of the commands

[HTML]/home/mickey# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]
[HTML]/home/mickey# lspci -v00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: fast devsel
	Memory at 44000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 10a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=168
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1870 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 2000 [size=256]
	Memory at b0114000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

06:09.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at b0115000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:09.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at b0114800 (32-bit, non-prefetchable) [size=2K]
	Memory at b0110000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

06:09.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, medium devsel, latency 57, IRQ 21
	Memory at b0116000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

06:0a.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0406
	Flags: bus master, medium devsel, latency 96, IRQ 23
	Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci, ath5k
[/HTML]

Please help a Newbie who struggles with the simplicity of linux

Thanks in advance.

---

