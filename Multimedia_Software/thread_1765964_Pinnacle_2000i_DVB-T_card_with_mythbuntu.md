---
title: "Pinnacle 2000i DVB-T card with mythbuntu"
date: 2011-05-23
forum: Multimedia Software
---

### Post by deviant085 on 2011-05-23
Hi all, i am trying to build myself a htpc box and i am having some problems with getting my DVB-T card to work with mythtv. I am running ubuntu 11.04 and i have just installed the mythbuntu components on top of the stock install. 

I can not for the life of me get it to work. and there really isn't much online about this card either. 

I check the mythtv wiki and it sent me to linuxtv.org for a complete list of compatible hardware. i did find my card on there but the info is about 5 years old :( 
[quote="linuxtv.org/wiki/index.php/DVB-T_PCI_Cards"]Not working so far (Oct.2006). Shows up as three unknown PCI devices ID 0040, 0041, 0042 with subsystems 0044. Manufacturer *Pinnacle Systems Inc.* detected correctly.[/quote]now i don't think this information is reverent anymore as you can see here
```
04:01.0 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 1
        Subsystem: Pinnacle Systems Inc. PCTV 2000i Dual DVB-T Pro PCI Tuner 1
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

04:01.1 Multimedia controller: Pinnacle Systems Inc. RoyalTS Function 2
        Subsystem: Pinnacle Systems Inc. PCTV 2000i Dual DVB-T Pro PCI Tuner 2
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fdefe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

04:01.2 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 3
        Subsystem: Pinnacle Systems Inc. PCTV 2000i Dual DVB-T Pro PCI Common
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fdefd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
```as you can see it is detecting it correctly. But nothing is showing up in mythtv... 

any thoughts??? 

Cheers...

EDIT: Or should i just get a new card, and trash this one?? if so, any suggestions?

---

