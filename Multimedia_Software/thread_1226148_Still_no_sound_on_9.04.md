---
title: "Still no sound on 9.04"
date: 2009-07-29
forum: Multimedia Software
---

### Post by kel_gb on 2009-07-29
Hi

I'm still without sound since upgrading from 8.10 to 9.04. I think maybe I need to install the correct driver as has been suggested for other users with similar issues, but cannot seem to find one.

I am using onboard sound and my motherboard is an Asus P5KPL-AM iG31

Can anyone help?

Cheers
Kel

(Btw, aplay -l and lspci -v outputs below (I don't pretend to know half of what this stuff means tho - noobie or what? LOL)) Hope that helps.

aplay -l gives:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kel@kel-desktop:~$ 

*****

lspci -v gives:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 82b0
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-fe9fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9ffbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: medium devsel, IRQ 11
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
	Subsystem: nVidia Corporation Device 0479
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8347
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	I/O ports at e800 [size=256]
	Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Memory at f8fe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: RaLink Device 2561
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febf8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

---

### Post by igorzwx on 2009-07-29
you may try to install another Ubuntu 9.04 in dual boot
and try OSS4 there, if your hardware is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

