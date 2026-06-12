---
title: "No Sound on  Ubuntu 6 or 7"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by fih on 2007-12-21
I'm a total newbie - please excuse any improprieties.
I have tried to live install Linux puppy, Fedora 8, and Ubuntu 6 and 7 to decide which distribution I should adopt. There are issues with all, but Ubuntu seems  to be the best choice for me. My main problem is that I cannot get my speakers to respond with Ubuntu, although they work well with other Linux distributions, and windows XP. 
I would welcome any help in this issue.
Thank you

---

### Post by Metaljaz on 2007-12-23
Tell us a few things more that maybe useful in an attempt to help you solve your problem:
What version of Ubuntu are you using? Is this a desktop or notebook computer with built in speakers or attached speakers? What type of sound card are you using?

---

### Post by leon_mcnichols on 2007-12-23
Got a Dell CPi PII 300 with 196 megs of ram a 20 gig hdd fresh install of Gusty. But I have no Audio yet the bios says it has a CS  4237B onboard. However I can't get to it to check it out to see if its in emu isa mode. Might be because I'm in docked mode. But here is a copy of the specs I got off sys info .

Any help would be cool. 

lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, prefetchable) [size=256M]

00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (prog-if 00 [VGA])
        Subsystem: Dell MagicGraph 128XD
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=16M]
        Memory at fde00000 (32-bit, non-prefetchable) [size=2M]
        Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]

00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
        Subsystem: Dell Unknown device 0074
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
        Subsystem: Dell Unknown device 0074
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 28000000-2bfff000 (prefetchable)
        Memory window 1: 2c000000-2ffff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at ece0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
        Flags: medium devsel, IRQ 9

00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell Unknown device 00a7
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at ec00 [size=128]
        Memory at fdcffc00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fe000000 [disabled] [size=128K]
        Capabilities: <access denied>


also the video?  slightly off topic but it says 16 meg prefetchable does this mean I can have shared video IE being a 16 meg Video settings so I could go past 800x600 ? Thanks guys in advance for the help.

---

### Post by Metaljaz on 2007-12-24
Read through this thread. Might be useful:

[http://ubuntuforums.org/showthread.php?t=328978](http://ubuntuforums.org/showthread.php?t=328978)

---

