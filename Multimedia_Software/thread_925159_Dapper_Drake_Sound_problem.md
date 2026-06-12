---
title: "Dapper Drake Sound problem"
date: 2008-09-20
forum: Multimedia Software
---

### Post by afrodeity on 2008-09-20
Does anybody know how to navigate through [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) to find the correct sound setup for the below? 

Output showing the Dapper Drake setup:

0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (r ev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev  03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff
        Prefetchable memory behind bridge: 20000000-200fffff

0000:00:03.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 42)
        Subsystem: D-Link System Inc DFE-530TX rev B
        Flags: bus master, medium devsel, latency 64, IRQ 11sudo modprobe snd-via82xx.
        I/O ports at 2400 [size=256]
        Memory at 41100000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 20100000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) ( prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 2020 [size=16]

0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2000 [size=32]

0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 0000
        Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 6 6, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <available only to root>

---

