---
title: "No sound"
date: 2009-10-17
forum: Multimedia Software
---

### Post by Ali Kante on 2009-10-17
Hi,

I've just installed BT4prefinal (based on Kubuntu) inside VirtualBox on a MacBookPro Host. Everything runs pretty fine, except the sound. I'm glad, if someone could help me here. :P
```

lspci -v
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
        Subsystem: Intel Corporation Device 0000
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at d100 [size=256]
        I/O ports at d200 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
``````
modinfo soundcore
filename:       /lib/modules/2.6.29.4/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
depends:
vermagic:       2.6.29.4 SMP mod_unload 686
```any suggestions very welcome.

---

### Post by Ali Kante on 2009-10-18
No ideas? :-(

---

### Post by Ali Kante on 2009-10-21
Problem solved:

You had to add the user to the sound group. :mad:

---

