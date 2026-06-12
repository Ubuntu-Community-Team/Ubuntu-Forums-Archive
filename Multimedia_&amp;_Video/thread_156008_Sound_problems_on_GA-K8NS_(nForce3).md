---
title: "Sound problems on GA-K8NS (nForce3)"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by konrads on 2006-04-06
Hello,
At first, ubuntu detected sound and installed it. But i could not get any microphone working for Skype. I tried the Recording Level Monitor to see if anything come through - nothing. As usual, i unmuted all channels, cranked the volume to max, but  - nothing. Then I started reading here on forums and some suggested creating the /etc/asound.conf after much fiddling with it, i got nothing. Instead, my max sound level now is very very low. I removed the asound.conf, but nothing changed.
I also don't have the ACL850 realtek mixer visible anymore. Should it even be there?

So, questions are:
[LIST=1]
[*]How to get my sound level back
[*]How to have my mic working?
[/LIST]


=== lspci -v BEGIN ===
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=32M]
	Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
	Subsystem: Giga-byte Technology: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
	Subsystem: Giga-byte Technology: Unknown device 0c11
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 9000 [size=32]
	I/O ports at 1c00 [size=64]
	I/O ports at 2000 [size=64]
	Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology: Unknown device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f5004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology: Unknown device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f5005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology: Unknown device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f5000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <available only to root>

0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
	Subsystem: Giga-byte Technology: Unknown device e000
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f5001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 9c00 [size=8]
	Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
	Subsystem: Giga-byte Technology: Unknown device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
	I/O ports at a000 [size=256]
	I/O ports at a400 [size=128]
	Memory at f5002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology: Unknown device 5002
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at f000 [size=16]
	Capabilities: <available only to root>

0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology: Unknown device b002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at c000 [size=16]
	I/O ports at c400 [size=128]
	Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 16
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
	Memory behind bridge: f2000000-f4ffffff
	Prefetchable memory behind bridge: e0000000-efffffff

0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Flags: fast devsel
	Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0221 (rev a1) (prog-if 00 [VGA])
	Subsystem: Asustek Computer, Inc.: Unknown device 81c7
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 5
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <available only to root>
=== lspci -v END ===

---

