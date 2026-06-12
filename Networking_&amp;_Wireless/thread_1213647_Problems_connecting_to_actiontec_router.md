---
title: "Problems connecting to actiontec router"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by floundering on 2009-07-15
I just migrated to Feisty Fawn from Vista, and it's having issues detecting my router (an actiontec, the default router Verizon gives you for fios. From what I've read in the little  documentation I found, a somewhat similar problem of decreased performance with Ubuntu is somewhat typical of my router type. "Somewhat" because it's not quite the same thing as the card refusing to recognize anything). My wireless card finds other networks in the area, but not my router's...the wireless settings are set to broadcast, and I never had problems with range on Vista. I mean, the networks I'm finding are more walls away than my router. Other wireless devices in the room can tap into it as well, so a mysterious wireless boogeyman didn't materialize during installation.

I'm on a Gateway M-6570****. The (relevant) output from an lspci:
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1000
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945 
```

Any guesses at what's causing the trouble?

---

### Post by superprash2003 on 2009-07-15
its better you get 9.04 , fiesty is a pretty old version.. you would get support on either 8.10 or 9.04

---

### Post by floundering on 2009-07-15
That was Pavlovian. I'm on Jaunty Jackalope, but run Feisty Fawn for a while...I just reflexively named Feisty as my os.

---

