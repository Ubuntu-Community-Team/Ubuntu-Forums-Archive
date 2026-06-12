---
title: "Modulartech MM200 TV card (or any PCI TV card)"
date: 2008-11-30
forum: Multimedia Software
---

### Post by noriek on 2008-11-30
Hello all,

Have had Ubuntu 8.1 installed, running fine, all video and sound present and correct. Whacked in my rather ancient modulartech MM200 tv card (the card that used pci bus for sound) and restarted but no joy with pic or sound. I've tried both xawtv and TVtime.

lspci -v | less shows the card is present:
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
        Subsystem: Modular Technology Holdings Ltd Device 0101
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e2000000 (32-bit, prefetchable) [size=4K]
        Kernel driver in use: bttv
        Kernel modules: bttv

00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
        Subsystem: Modular Technology Holdings Ltd Device 0101
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e2001000 (32-bit, prefetchable) [size=4K]


So now what??


Thanks

---

