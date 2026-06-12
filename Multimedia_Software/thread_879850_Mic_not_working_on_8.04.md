---
title: "Mic not working on 8.04"
date: 2008-08-04
forum: Multimedia Software
---

### Post by humaneasy on 2008-08-04
Mic does not work but everything else works with the sound.
Already tested a lot of options and follow the hints I found here and nothing seems to make it work.

```
aplay -l
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

```
 lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: d0000000-efffffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fc000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fa000000-fbffffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 70000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at c000 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c800 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at d000 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: medium devsel, IRQ 9
	I/O ports at 0500 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9202
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fc001000 (32-bit, non-prefetchable) [size=512]
	Memory at fc002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA controller])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9a20
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9a21
	Flags: 66MHz, medium devsel
	Memory at e0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at f9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9207
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at fb001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9207
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at a000 [size=256]
	Memory at fb000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at fa000000 [disabled] [size=64K]
	Capabilities: <access denied>

```

Can anyone tell me what to do?

---

