---
title: "Asus P5N32-E onboard sound issue"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by ThatGuyOnTheRoof on 2008-01-29
Hello everyone,

I've spent the last several hours searching to see if anyone has had the same problem with me, and further to see if anyone has solved this problem.  So, here is my problem:  The on-board sound isn't recognized by Ubuntu at all.  My motherboard is an Asus P5N32-E SLi Plus.  To my understanding, it should be using the snd-hda-intel module, but loading that module does nothing.

I've taken all the steps mentioned in [this thread (Comprehensive Sound Problem Solution Guide)]("http://ubuntuforums.org/showthread.php?t=205449") and have checked the BIOS settings to ensure that the card is enabled, and it seems to work properly in windows.  No, I don't have my sound muted, either. :confused:

Anyway, thanks in advance for any help that's given.  PS: Please don't stop in to tell me that your P5N32-E's on-board sound worked out of the box.  That's great and I wish we were all so fortunate, but that doesn't help me or anyone else that may be having this problem. :)

I'm about ready to scrap using Ubuntu for a while, even with as much as I liked prior releases, but Gutsy has been difficult from the get-go.  So anyway, if anyone can help me, I'd appreciate it.  And before anyone asks:

```
jason@dilettante:~$ sudo lspci -v
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: eb000000-edffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: efc00000-efcfffff
        Prefetchable memory behind bridge: 00000000ef900000-00000000ef9fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: efe00000-efefffff
        Prefetchable memory behind bridge: 00000000efd00000-00000000efdfffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [dc] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at ff00 [size=64]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c80 [size=64]
        Capabilities: [44] Power Management version 2

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at effff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at efffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at f700 [size=16]
        Memory at efffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at f200 [size=16]
        Memory at efffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at f100 [size=8]
        I/O ports at f000 [size=4]
        I/O ports at ef00 [size=8]
        I/O ports at ee00 [size=4]
        I/O ports at ed00 [size=16]
        Memory at efffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: efb00000-efbfffff
        Prefetchable memory behind bridge: efa00000-efafffff
        Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
        Capabilities: [8c] HyperTransport: MSI Mapping

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at efffa000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Memory at efff9000 (32-bit, non-prefetchable) [size=256]
        Memory at efff8000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at efff7000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at eb00 [size=8]
        Memory at efff6000 (32-bit, non-prefetchable) [size=256]
        Memory at efff5000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: ef800000-ef8fffff
        Prefetchable memory behind bridge: 00000000ef700000-00000000ef7fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: ef600000-ef6fffff
        Prefetchable memory behind bridge: 00000000ef500000-00000000ef5fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: ef400000-ef4fffff
        Prefetchable memory behind bridge: 00000000ef300000-00000000ef3fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: ef200000-ef2fffff
        Prefetchable memory behind bridge: 00000000ef100000-00000000ef1fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: ef000000-ef0fffff
        Prefetchable memory behind bridge: 00000000eef00000-00000000eeffffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: nVidia Corporation Unknown device 02c2
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at eb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ec000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at df00 [size=128]
        [virtual] Expansion ROM at edfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at efbff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at cf00 [size=128]
        Capabilities: [50] Power Management version 2

0a:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: nVidia Corporation Unknown device 02c2
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at e9000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 4f00 [disabled] [size=128]
        [virtual] Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0
```

And:

```
jason@dilettante:~$ aplay -l
aplay: device_list:204: no soundcards found...
```

---

