---
title: "Hauppauge HVR-1500 HD TV card"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by jonlowe on 2008-04-11
Has anyone gotten the Hauppauge HVR-1500 HD card working in Ubuntu on a laptop?  Or the HP Expresscard (same as the Hauppauge)?  Any help would be greatly appreciated with a detailed howto.  I've searched the net, tried several things, even got the firmware to load, but can't get it to work.  Works great in Vista.

Jon

---

### Post by jonlowe on 2008-04-18
Bump.  Anyone?  I'm desparate!

---

### Post by xc3RnbFO8P on 2008-04-18
Bad news:
[http://www.linuxtv.org/wiki/index.php/Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge")

---

### Post by jonlowe on 2008-04-18
I saw that, but elsewhere on Linux TV they talk about how support has been added in the latest drivers.  The wiki yu sent me to had that entry updated in August 2007, and the 1500 was added after that.

---

### Post by xc3RnbFO8P on 2008-04-18
Hardy Heron:
[http://news.softpedia.com/news/Linux-kernel-2-6-25-Released-83599.shtml]("http://news.softpedia.com/news/Linux-kernel-2-6-25-Released-83599.shtml")

---

### Post by jonlowe on 2008-04-19
Got it to work, ATSC only, no analog.  Use Ubuntu 8.04, and install the latest drivers from LinuxTV.org.  Use very latest Me-TV to autoscan and watch.

Jon

---

### Post by gabr10 on 2008-05-02
Same problem here
I'll give it a try on 8.04 but updating to the latest kernel which is supposed to support this card (2.6.25.1), I'll let you know the outcome later

---

### Post by bdoe on 2008-05-30
*bump*

Any luck with this?

I can't seem to be able to come up with the proper combination of drivers or firmware for this thing.  Here's my lspci output if it helps:
```
04:00.0 Multimedia video controller [0400]: Conexant Unknown device [14f1:8852] (rev 02)
    Subsystem: Hauppauge computer works Inc. Unknown device [0070:7797]
    Flags: fast devsel, IRQ 17
    Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=2M]
    Capabilities: [40] Express Endpoint IRQ 0
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```
So, my system sees the card, but can't seem to find the right drivers for it.  Someone mentioned downloading them from linuxtv.org, but...  which ones?

---

