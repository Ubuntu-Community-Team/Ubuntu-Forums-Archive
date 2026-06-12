---
title: "Optiplex 755 (Quad Core) - Ubuntu 7.10 (Still cannot get sound to work) -"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by SLK55_AMG on 2008-04-01
:confused:
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
	Subsystem: Dell Unknown device 0211
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Dell Unknown device 0211
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
	Subsystem: Dell Unknown device 0211
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fedad000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
	I/O ports at fe80 [size=8]
	I/O ports at fe90 [size=4]
	I/O ports at fea0 [size=8]
	I/O ports at feb0 [size=4]
	I/O ports at fef0 [size=16]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ec98 [size=8]
	Memory at febda000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
	Subsystem: Dell Unknown device 0211
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at febdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] #13 [0306]

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff00 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at febd9c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0211
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Dell Unknown device 0211
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff80 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: [50] Subsystem: Dell Unknown device 0211

00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=16]
	I/O ports at eca0 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] #13 [0306]

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 0211
	Flags: medium devsel, IRQ 9
	Memory at febd9b00 (64-bit, non-prefetchable) [size=256]
	I/O ports at ece0 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 0211
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe40 [size=8]
	I/O ports at fe50 [size=4]
	I/O ports at fe60 [size=8]
	I/O ports at fe70 [size=4]
	I/O ports at fed0 [size=16]
	I/O ports at ecb0 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] #13 [0306]

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c1 (prog-if 00 [VGA])
	Subsystem: Dell Unknown device 0d02
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
:confused:








ryan@cisco:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryan@cisco:~$ 



any ideas? no matter what i do, i never get sound.....nothing comes out the internal speakers.

---

### Post by jacob01 on 2008-04-01
The only sound that is supposed to come out of internal speakers is beeps. Are you talking about integrated sound card?

---

