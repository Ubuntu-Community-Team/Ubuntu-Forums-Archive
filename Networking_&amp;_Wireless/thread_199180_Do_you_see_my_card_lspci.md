---
title: "Do you see my card? lspci"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by iitywygms on 2006-06-18
kevin@kevin-laptop:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:09.0 Network controller: Intersil Corporation ISL3886IK (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

I have a prism wireless card and I am not sure if dapper knows it is there.  I dont see it, if it is not here, how do I get it to show up?  It use to work in breezy.
Latest Dapper, presario 2100 laptop.

---

### Post by iitywygms on 2006-06-18
A little more info

kevin@kevin-laptop:~$ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0400000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin USB
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Memory at d0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Modem Device
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <available only to root>

0000:00:09.0 Network controller: Intersil Corporation ISL3886IK (rev 01)
        Subsystem: Intersil Corporation: Unknown device 0000
        Flags: medium devsel, IRQ 9
        Memory at d0000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 24010000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin IDE
        Flags: bus master, medium devsel, latency 32
        I/O ports at 8080 [size=16]
        Capabilities: <available only to root>

0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Pavilion ze4400
        Flags: medium devsel

0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 8c00 [size=256]
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 24000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

---

### Post by iitywygms on 2006-06-18
I swithched cards.
used this link
[http://www.ubuntuforums.org/showthread.php?t=189070&highlight=broadcom+4306](http://www.ubuntuforums.org/showthread.php?t=189070&highlight=broadcom+4306)
all is good now.

---

