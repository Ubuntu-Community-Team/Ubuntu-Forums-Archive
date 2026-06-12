---
title: "No sound in Flash on any web browser"
date: 2011-05-27
forum: Multimedia Software
---

### Post by benjabean1 on 2011-05-27
This is driving me NUCKING FUTS!!:mad: I cannot figure out how to get sound working from Adobe Flash on Ubuntu 11.04 Desktop! No matter what browser I use, I still get no sound in flash on *any* browser!](*,)

```

benjamin@benjamin-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 30d0 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, fast devsel, latency 0
	Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Conexant Systems, Inc. Presario C700
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 91300000-923fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 92404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 91200000-912fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 30b8 [size=8]
	I/O ports at 30dc [size=4]
	I/O ports at 30b0 [size=8]
	I/O ports at 30d8 [size=4]
	I/O ports at 3020 [size=32]
	Memory at 92404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: medium devsel, IRQ 11
	Memory at 92404c00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Presario C700
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 1000 [size=256]
	Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

```

benjamin@benjamin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2011-05-27
This look familiar:
[http://ubuntuforums.org/showthread.php?p=10870131](http://ubuntuforums.org/showthread.php?p=10870131)

---

### Post by benjabean1 on 2011-05-28
Thanks so much lidex! Now I'm so satisfied I can bring myself to eat popcorn!:popcorn:

---

