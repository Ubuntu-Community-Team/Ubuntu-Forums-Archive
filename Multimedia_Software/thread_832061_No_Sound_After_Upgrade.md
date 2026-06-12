---
title: "No Sound After Upgrade"
date: 2008-06-17
forum: Multimedia Software
---

### Post by bazookapenguin on 2008-06-17
Hi everyone, after I upgraded from 7.10 to 8.04, I lost my sound. I followed the "Comprehensive Sound Guide" but that did work. I even compiled my driver but to no avail.

So I was wondering if you guys could help me get my sound back. Here's what I get after lspci -v
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
	Subsystem: Dell Unknown device 010c
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ff900000-ffafffff
	Prefetchable memory behind bridge: f0000000-f7ffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff600000-ff8fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 010c
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 010c
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
	Subsystem: Dell Unknown device 010c
	Flags: medium devsel, IRQ 10
	I/O ports at ccd0 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 010c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff60 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
	Subsystem: Dell Unknown device 010c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at c800 [size=256]
	I/O ports at cc40 [size=64]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Radeon AIW
	Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at ec00 [size=256]
	Memory at ff980000 (32-bit, non-prefetchable) [size=512K]
	Expansion ROM at ff900000 [disabled] [size=128K]
	Capabilities: <access denied>

02:08.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
	Subsystem: GVC Corporation Unknown device 0219
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at ff7f0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at dcf8 [size=8]
	Capabilities: <access denied>

02:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
	Subsystem: Intel Corporation EtherExpress PRO/100+ Management Adapter
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at ff7ef000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at dc80 [size=64]
	Memory at ff600000 (32-bit, non-prefetchable) [size=1M]
	[virtual] Expansion ROM at ff800000 [disabled] [size=1M]
	Capabilities: <access denied>

02:0a.0 Network controller: AIRONET Wireless Communications Cisco Aironet 340 802.11b Wireless LAN Adapter/Aironet PC4800 (rev 01)
	Flags: medium devsel, IRQ 17
	Memory at ff7eec00 (32-bit, non-prefetchable) [size=128]
	I/O ports at dc00 [size=128]
	I/O ports at d8c0 [size=64]

```

And after aplay -l

I get no soundcard found.

So can anyone help me?

Thanks!

---

