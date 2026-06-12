---
title: "Re: No Sound Output"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by falexge on 2006-10-19
This was the output when I typed the lspci command:

> [FONT="Lucida Console"]0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-feffffff
        Prefetchable memory behind bridge: f9000000-f9ffffff

0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at ffa0 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dce0 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        Capabilities: <available only to root>

0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: Dell 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=128]
        Memory at ff000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fb000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: Dell Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=256]
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <available only to root>[/FONT]

Which of them is the sound card and where can I get its drivers?

---

### Post by ReaderRat on 2006-10-19
> 0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
Subsystem: Dell Rage Pro Turbo AGP 2X
I would guess.

---

### Post by ReaderRat on 2006-10-19
Nevermind...

The ATI drivers help site is:  ATI - How to install the drivers
          [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

