---
title: "Need a little personalized sound help"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by infamousjre on 2007-11-16
I've followed pretty much every How To on the forums trying desperately to fix my sound but haven't had any luck. When I started out, sound worked with headphones, but I made it worse and now I'm stuck with nothing but a little speaker with a cross next to my clock.

"No Volume control GStreamer plugins and/or devices found." is the error I get.

and here's my lspci -v (minus a few things)

```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0400000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
        Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Rioworks Unknown device 2036
        Flags: medium devsel, IRQ 11
        I/O ports at 8400 [size=256]
        Memory at d0008000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Rioworks Unknown device 2033
        Flags: medium devsel, IRQ 5
        Memory at d0009000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
        Subsystem: Rioworks Unknown device 2036
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at ffbfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Rioworks Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d000c000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
        Subsystem: Rioworks Unknown device 2036
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 8080 [size=16]
        Capabilities: <access denied>

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Rioworks Unknown device 2036
        Flags: medium devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Rioworks Unknown device 2036
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

```

---

### Post by infamousjre on 2007-11-17
Actually got my device back by re-installing the alsa drivers, but I still have no sound. Anyone care to take a stab at this with me?

---

