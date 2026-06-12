---
title: "Sound no longer working"
date: 2009-04-15
forum: Multimedia Software
---

### Post by sailthesea on 2009-04-15
Hi 
 I lost sound in Ubuntu intrepid and was trying the stickies to get it back but I just can't seem to get the driver
 I was hoping someone might be able to give me a clue or better yet A line or two of code get things running again
 More info:

mark@ubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...

mark@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: e0000000-e7ffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
	Subsystem: Intel Corporation Device 4541
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
	I/O behind bridge: 0000e000-0000ffff
	Memory behind bridge: f4000000-fbffffff
	Prefetchable memory behind bridge: 30000000-39ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device 4541
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 3a000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Cirrus Logic Device 5959
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at d800 [size=256]
	I/O ports at dc80 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
	Subsystem: PCTel Inc Device 4c21
	Flags: medium devsel, IRQ 5
	I/O ports at d400 [size=256]
	I/O ports at dc00 [size=128]
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
	Subsystem: Dell Device 012a
	Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at c000 [size=256]
	Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
	Subsystem: Dell Device 012a
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at ec80 [size=128]
	Memory at f8fffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at 38000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Dell Device 012a
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: f4000000-f7fff000
	I/O window 0: 0000e000-0000e0ff
	I/O window 1: 0000e400-0000e4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Dell Device 012a
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at f8001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 3c000000-3ffff000
	I/O window 0: 0000e800-0000e8ff
	I/O window 1: 0000f000-0000f0ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

mark@ubuntu:~$ 

 Any help would be great !
Thanks

---

### Post by LostMagix on 2009-04-15
Did you try:

```
sudo alsa force-reload
```

---

### Post by LostMagix on 2009-04-15
sorry hasty post...

---

