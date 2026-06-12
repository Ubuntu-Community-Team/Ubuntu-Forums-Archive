---
title: "Sound Card Detected but not playing"
date: 2009-01-17
forum: Multimedia Software
---

### Post by mastergaurav on 2009-01-17
Hi,

I have Compaq Presario v3000 laptop. The problem is that the sound card has been detected but it does not play any audio.

I went through the "Comprehensive Guide" at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but to no avail.

Can somebody guide me... I'm running Ubuntu 8.10

Here are some results of the probes:

```

**root@indra:/home/gvaish# lspci -v**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0
	Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

[/B]00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30b2
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30b2
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: d4000000-d40fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30b2
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d4544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4100000-d41fffff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 30b2

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d4544400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Device 135b
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 7d-22-b6-ff-ff-02-13-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at d4100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: e100
	Kernel modules: e100

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d4101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at d4101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: medium devsel, IRQ 10
	Memory at d4101c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: medium devsel, IRQ 10
	Memory at d4102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

```

```

**root@indra:/home/gvaish# asoundconf list**
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel

```

```

**root@indra:/home/gvaish# aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

**root@indra:/home/gvaish# modprobe -l snd-hda-intel**
/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko

```





-Gaurav

---

