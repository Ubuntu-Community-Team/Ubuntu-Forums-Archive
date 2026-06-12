---
title: "No sound no matter what I try, SB450"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by InMSWeAntitrust on 2007-08-16
I've looked at every single SB450 thread out there, and haven't gotten anything regarding sound working on my Gateway MT3708 laptop.

Output of lspci -v:

```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0000000-c00fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0100000-c01fffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: b0000000-b1ffffff
        Prefetchable memory behind bridge: 00000000b2000000-00000000b3ffffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at c0507000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 19
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c0100000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 8225
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at b000 [size=256]
        Memory at c0200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>


```

I would really appreciate any response, as this is the only thing I really care about getting working with Ubuntu, everything else works fine, or as well as I need it.

---

