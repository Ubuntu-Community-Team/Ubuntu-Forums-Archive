---
title: "Strange sound on 9.10 with a AC'97 realtek audio card"
date: 2009-11-03
forum: Multimedia Software
---

### Post by DL21 on 2009-11-03
Hi,
I updated to 9.10 yesterday. Everything works fine, except sound...
When i launch a game like Tremulous or Nexuiz, sound works for 2 seconds and then, no sound.
I have a Realtek AC'97 sound card.
I noticed sound is also grabbled when I play music.
Can you help me ?
Thanks, DL21.

---

### Post by jemdos on 2009-11-03
I think I have the same problem, thought I've not tested with games.

If you have sorround enabled (4.0, 5,0, 5.1, 7.1...) try swapping back to simple analog stereo (at home at least, is the workaround I'm now using)

It would be helpful to show the readout of "aplay -l" and "lspci -v" in your computer.

---

### Post by DL21 on 2009-11-03
Switched to Analog Stereo Duplex to Analog Surround 5.1 Output, It worked, thanks.
Here are the outputs of the commands :
> [SIZE="5"]aplay -l :[/SIZE]
**** Liste des PLAYBACK périphériques ****
carte  0: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: SI7012 [SiS SI7012], périphérique 0 : Intel ICH [SiS SI7012]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

[SIZE="5"]lspci -v :[/SIZE]
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 32
	Memory at a0000000 (32-bit, non-prefetchable) [size=512M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-sis
	Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: d0000000-d1ffffff
	Prefetchable memory behind bridge: c0000000-cfffffff
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
	Flags: bus master, medium devsel, latency 0

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at d3000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 128
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Kernel driver in use: pata_sis

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
	Subsystem: Packard Bell B.V. Device 3054
	Flags: medium devsel, IRQ 18
	I/O ports at d000 [size=256]
	I/O ports at d400 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at d3001000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at d3002000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at d3003000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at d3004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e000 [size=256]
	Memory at d3005000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: rtl8180

00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Packard Bell B.V. Device e009
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at e400 [size=256]
	Memory at d3006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp

01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE AGP [Radeon HD 3450]
	Subsystem: ASUSTeK Computer Inc. Device 0028
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at d1000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: ASUSTeK Computer Inc. Device aa28
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d1010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



---

