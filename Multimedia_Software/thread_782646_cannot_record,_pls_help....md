---
title: "cannot record, pls help..."
date: 2008-05-05
forum: Multimedia Software
---

### Post by yssida on 2008-05-05
Good day everyone!

I cannot record audio from the sound recorder utility in Ubuntu Hardy.

I tried changing the settings but nothing works. What are the steps I should take?

---

### Post by presston on 2008-05-05
did you have installed alsa & config it?

---

### Post by yssida on 2008-05-05
I think there is ALSA installed. I can hear sounds, it's just this. I can't record, I don't know why. :(

This is the output of lspci -v
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 0000000050000000-00000000500fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f0400000-f04fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: medium devsel, IRQ 10
	Memory at 50100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at 2000 [size=256]
	Memory at f0200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1040
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f0400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

0a:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f0400800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f0400c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f0401000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

```

---

### Post by presston on 2008-05-05
you can have sound over OSS, but it's not good driver. if you didn't installed alsa - yol'll have no multiple sound, sound record etc.

you this to config

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by yssida on 2008-05-05
Yes, I read that. But I can't find a specific problem about recording.

---

### Post by presston on 2008-05-05
there is no specific problem for recording. its common problem of sound config. uoy must do all that HOWTO

---

