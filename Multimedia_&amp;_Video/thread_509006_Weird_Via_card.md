---
title: "Weird Via card?"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by xubu_caapn on 2007-07-24
Hey guys, I just installed Xubuntu on a friend's computer. Everything worked out of box, except video card. He seems to have a obscure video card or something? It's onboard, here is lspci -v:

```

01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 11) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at fbdf0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] AGP version 3.0


```

Now when I try and run the ncurses based xserver configuration thing, i pick a via video card, and in a number of configurations. It won't boot into X, the only way I can is if I choose the vesa driver. It isn't working properly though, a lot of flickering and things like that. Most applications sort of open in sheets, if you know what I mean. How do I find out exactly what this card is and how to configure it?

---

### Post by fredj on 2007-07-25
Look in the motherboard manual. If you don't have this you should be able to get a copy from the 
motherboard manufacturers website.

---

