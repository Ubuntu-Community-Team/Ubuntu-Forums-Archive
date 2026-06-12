---
title: "Sound Issues-IBM thinkCentre"
date: 2010-10-17
forum: Multimedia Software
---

### Post by vintcius on 2010-10-17
i am using ibm thincentre & Ubuntu 10.10
the issue that i m facing is that:

Symptoms:
1) I do have sound when I plug my earphones into the sound jack
2) But there is no sound with just the normal speakers inbuilt in the PC

Plzz help.

---

### Post by vintcius on 2010-10-17
These are the outputs that i got for the following commands:

vintcius@vintcius:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



vintcius@vintcius:~$ **lspci -v**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: IBM Device 02d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: IBM Device 02d9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 3800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 3440 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3460 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 34a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d03c0000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: d0000000-d00fffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at d03c0800 (32-bit, non-prefetchable) [size=512]
	Memory at d03c0400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Subsystem: IBM Device 02d9
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM Device 02d9
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 34f0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: IBM Device 02d9
	Flags: medium devsel, IRQ 9
	I/O ports at 34c0 [size=32]
	Kernel modules: i2c-i801

0a:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)
	Subsystem: IBM Device 02d9
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at d0000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

---

### Post by vintcius on 2010-10-18
sumbody plzz help!

---

