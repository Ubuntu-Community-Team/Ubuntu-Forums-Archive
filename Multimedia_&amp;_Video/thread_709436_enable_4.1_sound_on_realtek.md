---
title: "enable 4.1 sound on realtek??"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by strongboww on 2008-02-27
hi, i have problems enabling 4.1 sound on my ac97; i unmuted surround in alsamixer but still nothiing;

maybe i should add that i must connect the surround to the "blue"-thing on motherboard, worked fine after installing mobo drivers in winxp, i even would be happy if just duplicate front would work

tried to do the howto-soundproblems above but i cant find the current alsa-drivers

```
longbow@heimdall:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: nForce2 [NVidia nForce2], Gerät 0: Intel ICH [NVidia nForce2]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: nForce2 [NVidia nForce2], Gerät 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
longbow@heimdall:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ed003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ed004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ed005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 570c
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at ed000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d000 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at d400 [size=256]
        I/O ports at d800 [size=128]
        Memory at ed001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: eb000000-ecffffff
        Prefetchable memory behind bridge: 50000000-500fffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

01:08.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: 3Com Corporation 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c000 [size=128]
        Memory at ec000000 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. N6600GT TD 128M AGP
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <access denied>

longbow@heimdall:~$ 

```

---

### Post by superprash2003 on 2008-02-28
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

