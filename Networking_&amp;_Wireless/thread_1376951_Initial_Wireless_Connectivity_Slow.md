---
title: "Initial Wireless Connectivity Slow"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by ThinkBaz on 2010-01-09
I'm running Lucid Alpha 1.  Installed it about two weeks ago.  Until a few days ago, the wireless networking was the best I've witnessed on any o.s.  However, after last Wednesday's updates, connectivity now lags about 10-30 seconds whenever I open any web-page or access the repositories via aptitude.  Granted after it gets going, it's fine.  I noticed this same behavior in 9.10.  I tested my XP connection and found no problems.  Please help with any suggestions.

---

### Post by efflandt on 2010-01-09
You may get better help if you say what wireless device you have and which modules it is using (output related to your wireless device from **sudo lspci -v** or **sudo lsusb -v** depending whether it is built-in or external).  I don't think there are any general wireless issues, at least not in 9.10.

Also which wireless security method do you use and is SSID broadcast on your wireless router disabled (which really does not help security any and can result in lag, since your wireless cannot tell if it is still up without communicating with it).

---

### Post by ThinkBaz on 2010-01-09
> **efflandt said:**
> You may get better help if you say what wireless device you have and which modules it is using (output related to your wireless device from **sudo lspci -v** or **sudo lsusb -v** depending whether it is built-in or external).  I don't think there are any general wireless issues, at least not in 9.10.

Also which wireless security method do you use and is SSID broadcast on your wireless router disabled (which really does not help security any and can result in lag, since your wireless cannot tell if it is still up without communicating with it).

Short replies first:

wireless security is WPA/WPA2.

SSID is NOT disabled.

Please keep in mind, all was working quite well until some upgrades.

Thanks for your help.

$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: IBM Device 0575
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: IBM Device 058c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at a0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at a0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: IBM Device 058c
	Flags: fast devsel
	Memory at 20200000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: IBM Device 05b7
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at a0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: a0100000-a01fffff
	Prefetchable memory behind bridge: 0000000020000000-00000000201fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: IBM Device 05b8
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: a2000000-a3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: IBM Device 05b8
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=12, sec-latency=0
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: a4000000-a5ffffff
	Prefetchable memory behind bridge: 00000000b0100000-00000000b01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: IBM Device 05b8
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=13, subordinate=13, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: a6000000-a7ffffff
	Prefetchable memory behind bridge: 00000000d0100000-00000000d01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: IBM Device 05b8
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: IBM Device 0566
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at a0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=14, subordinate=17, sec-latency=64
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: a8000000-b00fffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: IBM Device 0568
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: IBM Device 056a
	Flags: bus master, 66MHz, medium devsel, latency 0
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: IBM Device 056b
	Flags: medium devsel, IRQ 11
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
	Subsystem: IBM Device 0577
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at a0100000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

13:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
	Subsystem: IBM Device 058a
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at a7f00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: IBM Device 056c
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=14, secondary=15, subordinate=16, sec-latency=176
	Memory window 0: d8000000-dbfff000 (prefetchable)
	Memory window 1: a8000000-abfff000
	I/O window 0: 00008000-000080ff
	I/O window 1: 00008400-000084ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10)
	Subsystem: IBM Device 0511
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at b0001000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

14:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
	Subsystem: IBM Device 0556
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at b0001800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

$

---

### Post by ThinkBaz on 2010-01-14
You know, when I was running Debian, I dismissed all the tripe about the Ubuntu forum.  However, looking at the responses, or lack-thereof, received here, I see they're more accurate that not.

---

