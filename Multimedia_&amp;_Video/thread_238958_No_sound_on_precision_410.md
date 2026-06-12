---
title: "No sound on precision 410"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by Juan Orozco on 2006-08-18
I've searched everywhere but no luck. I have a Dell Presicion 410 Pent. II, which has an integrated sound card that works on windows, but i cant even get it to be recognized by edubuntu. (nor any ubuntu). errors:
jporozco@edubuntu:~$ aplay -l
aplay: device_list:221: no soundcards found...
jporozco@edubuntu:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Subsystem: Dell: Unknown device 0080
        Flags: bus master, medium devsel, latency 64
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: f2000000-f5ffffff

0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at ffa0 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 185
        I/O ports at dce0 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
        Subsystem: Dell 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 185
        I/O ports at dc00 [size=128]
        Memory at fe000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000f1000000-00000000f1f00000
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 11) (prog-if 00 [VGA])
        Subsystem: Diamond Multimedia Systems RIVA TNT2/TNT2 Pro
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 161
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f4000000 (32-bit, prefetchable) [size=32M]
        Expansion ROM at f2000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:0a.0 SCSI storage controller: Adaptec AHA-2940U2/U2W / 7890/7891
        Subsystem: Dell: Unknown device 0080
        Flags: bus master, medium devsel, latency 64, IRQ 177
        BIST result: 00
        I/O ports at ec00 [disabled] [size=256]
        Memory at fafff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fb000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:0e.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)
        Subsystem: Adaptec AIC-7880P Ultra/Ultra Wide SCSI Chipset
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at e800 [disabled] [size=256]
        Memory at faffe000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at f1000000 [disabled] [size=64K]
        Capabilities: <available only to root>

i've noticed a couple of people having the same problem with this system but none in ubuntu and since i'm a newbee, cant translate the instructions from the other OS to Ubuntu ([http://www.linuxquestions.org/questions/showthread.php?t=284735)](http://www.linuxquestions.org/questions/showthread.php?t=284735)).
any clues that might help?

---

