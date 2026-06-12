---
title: "ES1988, cannot find sound card."
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by Antexter on 2008-01-21
So today I found that I had no sound, did some searching and found this [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
And it told me to post on the forum, because of the one I put in bold.

Any ideas on solving the problem, I really want to avoid reinstalling kubuntu.

> computer@KDElappy:~$ aplay -l
aplay: device_list:222: no soundcards found...
computer@KDElappy:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Subsystem: Compaq Computer Corporation Armada M700/E500
        Flags: bus master, medium devsel, latency 64
        Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 40000000-410fffff
        Prefetchable memory behind bridge: 28000000-280fffff

00:04.0 CardBus bridge: Texas Instruments PCI1211
        Subsystem: Compaq Computer Corporation Unknown device b103
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 41180000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3460 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 3440 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
        Subsystem: Compaq Computer Corporation Unknown device b114
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 3000 [size=256]
        Capabilities: <access denied>

00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
        Subsystem: Intel Corporation EtherExpress PRO/100 P Mobile Combo Adapter
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 41200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3400 [size=64]
        Memory at 41100000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>

00:09.1 Serial controller: Agere Systems LT WinModem (prog-if 00 [8250])
        Subsystem: Intel Corporation Unknown device 2201
        Flags: medium devsel, IRQ 11
        I/O ports at 3470 [size=8]
        Memory at 41280000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Armada M700
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 28000000 [disabled] [size=128K]
        Capabilities: <access denied>

computer@KDElappy:~$ sudo modprobe snd-ES1988
**FATAL: Module snd_ES1988 not found.**
computer@KDElappy:~$  

Edit: I looked at alsa and its the latest one.

---

### Post by Antexter on 2008-01-22
I think this is posted in the wrong section itsn't it, would be better at home in general I believe.

Possible anyone can move this, or help with the problem :).

Thanks.

---

### Post by Antexter on 2008-01-23
This is a attempt to bump the thread as not having sound is very annoying!

---

