---
title: "No sound? Please help."
date: 2009-01-25
forum: Multimedia Software
---

### Post by MikeylovesJade on 2009-01-25
Hi, well i installed ubuntu and i had sound for awhile but all of a sudden it doesnt anymore, nothings muted n shows where i can turn the volume up n down still n i've even tryed changing speakers n even as much as trying a head set but nothing works.

I found some site where it told me to put a command in the terminal just to make sure it displays a sound card n it does n says its working fine but no matter what i do no sound comes out.


Edit: When i type aplay -l it says


open@terminator:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
open@terminator:~$


another Edit n more info:

open@terminator:~$ sudo lspci -v
[sudo] password for open: 
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 30100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ffe0 [size=8]
	Memory at 20000000 (32-bit, prefetchable) [size=256M]
	Memory at 30180000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
	Kernel modules: intelfb

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 301c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 30200000-302fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: 30300000-303fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 30400000-304fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 30500000-305fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 301c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 30000000-300fffff
	Capabilities: [50] Subsystem: Gateway 2000 Device 4037

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 20b0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 20c8 [size=8]
	I/O ports at 20ec [size=4]
	I/O ports at 20c0 [size=8]
	I/O ports at 20e8 [size=4]
	I/O ports at 20a0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: medium devsel, IRQ 10
	I/O ports at 2000 [size=32]
	Kernel modules: i2c-i801

05:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
	Subsystem: Conexant Systems, Inc. Device 2000
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 11
	Memory at 30000000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 1040 [size=8]
	Capabilities: [40] Power Management version 2

05:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 17
	Memory at 30011000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
	Subsystem: Gateway 2000 Device 4037
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at 30010000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: e100
	Kernel modules: e100

---

### Post by MikeylovesJade on 2009-01-25
Also i tried, chmod o+rw /dev/audio but says operation not permitted

---

