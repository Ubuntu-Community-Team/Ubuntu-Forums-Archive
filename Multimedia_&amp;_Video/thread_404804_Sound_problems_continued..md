---
title: "Sound problems continued."
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by Salo on 2007-04-08
1. - Surround Sound and bad quality:
I followed the comprehensive guide to sound problems and that got my sound working with my audigy se, ca0106 driver. But now, I only get sound from my left and right speakers and near crap quality, and nothing from the sub/rear/side speakers.

Things I have done:

Alsa mixer has all the IEC options unchecked, all the channels either unmuted or turned up.

Volume control has the channels turned up and unmuted

I turned my overall system volume down to a little over half and that seems to do the quality, but much finer sounds or parts of a song or movie that get to high or to low turn into crackles and static.


This really is the only thing stopping me from a complete switchover

help is appreciated, thanks for everything guys.

Some outputs that might be helpful:


aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] Vendor Specific Information
        Capabilities: [a0] AGP version 3.0

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: e8000000-f7ffffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: AOPEN Inc. Unknown device 040a
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at fa100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa000000-fa0fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at f000 [size=16]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: AOPEN Inc. Unknown device 042e
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 169
        I/O ports at c000 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at d000 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: AOPEN Inc. Unknown device 042d
        Flags: medium devsel, IRQ 12
        I/O ports at 5000 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc R420 JJ [Radeon X800SE] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 2610
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 12
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

01:00.1 Display controller: ATI Technologies Inc Unknown device 4a6a
        Subsystem: PC Partner Limited Unknown device 2611
        Flags: 66MHz, medium devsel
        Memory at f0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at f9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: AOPEN Inc. Unknown device 03ee
        Flags: bus master, medium devsel, latency 32, IRQ 201
        I/O ports at a000 [size=256]
        Memory at fa010000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 185
        I/O ports at a400 [size=32]
        Capabilities: [dc] Power Management version 2

02:0a.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1d
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at fa000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

```

---

