---
title: "Ubuntu 8.04 64-Bit  Wireless Not Working"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by mgoblue on 2009-01-06
sudo lspci -v gives:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [44] HyperTransport: MSI Mapping
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Unknown device ff50

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0400000-f04fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [b8] HyperTransport: MSI Mapping

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [b8] HyperTransport: MSI Mapping

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: f0100000-f01fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Unknown device ff50
	Capabilities: [b8] HyperTransport: MSI Mapping

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8430 [size=8]
	I/O ports at 8424 [size=4]
	I/O ports at 8428 [size=8]
	I/O ports at 8420 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f0208000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] #12 [0010]

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0004000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0005000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0208400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0006000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0007000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0208800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0b, sec-latency=64
	Memory behind bridge: f0500000-f05fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] #0f [0010]

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 508
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: [48] Power Management version 3
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [c0] Express Legacy Endpoint IRQ 0

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint IRQ 0
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f0501000 (32-bit, non-prefetchable) [size=4K]
	Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2

09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, slow devsel, latency 64, IRQ 20
	Memory at f0500800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2

09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: slow devsel, IRQ 11
	Memory at f0502000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2


```

---

### Post by mgoblue on 2009-01-07
Anyone got any advice?

---

### Post by mgoblue on 2009-01-09
Bump

---

### Post by mgoblue on 2009-01-10
Bump.

---

### Post by mgoblue on 2009-01-11
Bump..

---

### Post by mgoblue on 2009-01-12
Last bump.. then I'm just creating a new topic next time D=

---

