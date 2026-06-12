---
title: "Can't Get Sound Working"
date: 2008-08-26
forum: Multimedia Software
---

### Post by catapultj on 2008-08-26
Hi-

I've just installed Ubuntu (8.04) and I'm having trouble getting sound to work. I followed the instructions in the "Comprehensive Sound Problems" thread at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I'm not having any luck.

Here's what I did:

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

```
lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: fd000000-feafffff
	Prefetchable memory behind bridge: d8000000-efffffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fcf00000-fcffffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device 0174
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at df40 [size=64]
	Capabilities: <access denied>

```

I'm assuming that my soundcard chipset is the Intel ICH5. So I typed

```
sudo modprobe sudo modprobe snd-intel8x0
```

This didn't work. I ran alsamixer, made sure that levels are up. I don't know what to do next. Does anyone have any suggestions, tips, or hints?

-jason.

---

### Post by catapultj on 2008-08-26
i got it working. I went into alsamixer and just unmuted *everything*

---

