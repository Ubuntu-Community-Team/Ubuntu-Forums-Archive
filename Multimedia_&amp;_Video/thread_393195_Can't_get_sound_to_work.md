---
title: "Can't get sound to work"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by Bungo Pony on 2007-03-25
I'm very new to Ubunto, so please bear with me.

I can't get my onboard sound to work. It's made by realtek. I tried downloading drivers, but I'm pretty much lost on how to use them. Could I please get some help?

---

### Post by kipriano on 2007-03-25
i installed m soundcard so i can play sound in surround mode. but now i can't play sounds at all. what should i do? does ubuntu have sistem restore like windows? please help i am desperate

---

### Post by r4ik on 2007-03-25
> **Bungo Pony said:**
> I'm very new to Ubunto, so please bear with me.

I can't get my onboard sound to work. It's made by realtek. I tried downloading drivers, but I'm pretty much lost on how to use them. Could I please get some help?

Could  post   lspci -v please ?
It might give others some info nothing more i can do for you.

[http://www.ubuntuforums.org/showthread.php?t=350526&highlight=place+screenshot](http://www.ubuntuforums.org/showthread.php?t=350526&highlight=place+screenshot)

good luck !

---

### Post by Bungo Pony on 2007-03-25
> Could post lspci -v please ?

First, I'd like to know exactly what that does. System specs?

Second, here ya go:

00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at fc00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at f400 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fd800000-fd8fffff
        Prefetchable memory behind bridge: fdf00000-fdffffff
        Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000fdd00000-00000000fdd00000
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdb00000
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd900000
        Capabilities: <access denied>

00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 2601
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
        Subsystem: D-Link System Inc DFE-530TX rev C
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 233
        I/O ports at cc00 [size=256]
        Memory at fd8ff000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fdf00000 [disabled] [size=64K]
        Capabilities: <access denied>

01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 1013
        Flags: bus master, medium devsel, latency 64, IRQ 50
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 8056
        Flags: bus master, medium devsel, latency 64, IRQ 225
        Memory at fd8fe000 (32-bit, non-prefetchable) [size=2K]
        Memory at fd8f8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
        Subsystem: Elitegroup Computer Systems Unknown device 8056
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at ac00 [size=256]
        [virtual] Expansion ROM at fdb00000 [disabled] [size=128K]
        Capabilities: <access denied>


edit: I removed the SB card because only drivers for Windows Vista currently exist.

---

### Post by Bungo Pony on 2007-03-25
Nevermind. Got it to work following this:

[http://www.ubuntuforums.org/showthread.php?t=390625&highlight=realtek+sound](http://www.ubuntuforums.org/showthread.php?t=390625&highlight=realtek+sound)

---

