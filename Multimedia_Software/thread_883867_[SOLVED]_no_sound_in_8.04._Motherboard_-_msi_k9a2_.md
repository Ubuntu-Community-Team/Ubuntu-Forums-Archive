---
title: "[SOLVED] no sound in 8.04. Motherboard - msi k9a2 platinum"
date: 2008-08-08
forum: Multimedia Software
---

### Post by OliverN on 2008-08-08
[SOLVED] - Ubuntu only sends output through motherboard back I/O port...

I need sound, but I have no idea how to get it.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
	Subsystem: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
	Flags: bus master, 66MHz, medium devsel, latency 0
	Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe700000-fe7fffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: fe800000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=8]
	I/O ports at 7000 [size=4]
	I/O ports at 6000 [size=16]
	Memory at fe6ff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe6fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe6fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe6fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe6fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe6fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe6ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7376
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 376c
	Flags: bus master, fast devsel, latency 0, IRQ 218
	I/O ports at b800 [size=256]
	Memory at fe7ff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe7c0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 PCI bridge: PLX Technology, Inc. PEX 8547 48-lane, 3-port PCI Express Switch (rev aa) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Memory at fe8e0000 (32-bit, non-prefetchable) [size=128K]
	Bus: primary=02, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: <access denied>

03:00.0 PCI bridge: PLX Technology, Inc. PEX 8547 48-lane, 3-port PCI Express Switch (rev aa) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

03:0c.0 PCI bridge: PLX Technology, Inc. PEX 8547 48-lane, 3-port PCI Express Switch (rev aa) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

04:00.0 Display controller: ATI Technologies Inc R680 [Radeon HD 3870 x2]
	Subsystem: ATI Technologies Inc Unknown device 2042
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at c000 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: ATI Technologies Inc R680 [Radeon HD 3870 x2] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device 2542
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at d000 [size=256]
	Expansion ROM at feac0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
	Subsystem: ATI Technologies Inc Radeon HD 3870 Audio device
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at feaec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 376d
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at e800 [size=128]
	Capabilities: <access denied>
```

---

### Post by OliverN on 2008-08-21
bump.

the problem is shared between the distros I have installed; Ubuntu, Fedora and openSUSE.

Can someone recommend a special driver, or walk me through sound testing?

---

