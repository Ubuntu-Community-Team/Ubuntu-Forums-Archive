---
title: "Just another &quot;no sound&quot; problem"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by ktm5124 on 2006-08-18
So I have no sound.

Here's the output from lspci -v:
> 
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] #09 [4104]
        Capabilities: [a0] AGP version 2.0

0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: e8000000-efffffff

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Prefetchable memory behind bridge: 40000000-43ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 44000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Flags: medium devsel, IRQ 5
        I/O ports at b400 [size=256]
        I/O ports at b080 [size=128]
        Capabilities: [50] Power Management version 2

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell: Unknown device 8127
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at fa000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 40000000-41fff000 (prefetchable)
        Memory window 1: f6000000-f7fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
        Subsystem: Dell: Unknown device 01be
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at fa001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 42000000-43fff000 (prefetchable)
        Memory window 1: f8000000-f9fff000
        I/O window 0: 0000d800-0000d8ff
        I/O window 1: 0000dc00-0000dcff
        16-bit legacy interface ports at 0001

0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corporation: Unknown device 2721
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at faffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

My volume is not muted. When I went into Multimedia Systems Selector and clicked the test sound no sound was played. When I go to Multimedia Systems Selector by entering "gstreamer-properties" in terminal, I get the output:
> 
(gstreamer-properties:8260): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'

What also may be of interest is that I don't have an /etc/asound.conf file but when someone added one in that person said he/she got errors so I don't want to do that till I know it's something I need =p.

I've read through a lot of threads on sound issues. Anyone have any ideas from the given information? Need more?

---

