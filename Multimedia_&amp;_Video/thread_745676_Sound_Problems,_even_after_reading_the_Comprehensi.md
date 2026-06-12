---
title: "Sound Problems, even after reading the Comprehensive Sound Problems thread"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by OvenMitt Bandit on 2008-04-04
I have read the Comprehensive Sound Problems Solutions guide, and I am still having issues. My sound cards are detected properly, and since I have multiple sound cards, I made sure the correct order has been set in /etc/modprobe.d/alsa-base. Still nothing.

Here is the printout of my aplay -l :

```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And here is the printout of lspci -v :

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
        Memory behind bridge: dbd00000-dfefffff
        Prefetchable memory behind bridge: bba00000-dbbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dfffe000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 1800
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: ABIT Computer Corp. Unknown device 7403
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d000 [size=256]
        Memory at dfffbf00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04) (prog-if 10 [OHCI])
        Subsystem: Indigita Corporation FireWire Host Bus Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at dfffa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: D-Link System Inc Unknown device 3b09
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at dffe0000 (32-bit, non-prefetchable) [size=64K]
        Memory at dffb0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dc00 [size=8]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 22
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at dfee0000 [disabled] [size=128K]
        Capabilities: <access denied>

```

If anyone can help me out, it will be greatly appreciated.

Thanks!

---

