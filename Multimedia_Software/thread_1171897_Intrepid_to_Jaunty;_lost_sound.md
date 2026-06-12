---
title: "Intrepid to Jaunty; lost sound"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Saint_ on 2009-05-27
Upgraded to Jaunty a few hours ago and so far it seems faster than Intrepid, so I'm diggin it. But I'm completely soundless once I boot into Ubuntu (but my speakers do work). I've checked through several other threads but they were all specified towards intel audio chips; whereas lspci -v returns
```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: Hewlett-Packard Company Device 30f2            
        Flags: bus master, fast devsel, latency 0, IRQ 19         
        Memory at d2310000 (32-bit, non-prefetchable) [size=16K]  
        Capabilities: <access denied>                             
        Kernel driver in use: HDA Intel                           
        Kernel modules: snd-hda-in

```

So to blatently state the obvious, I do not have an intel chip and quite oddly enough I haven't seen any other threads dealing with the Azalia controller (though it's quite possible I simply missed the thread that does). Also, in alsamixer I've got all my sounds cranked up to 100, so that's not the problem either. I'm speculating it might be a bug, but that's just a guess. Anyways, any and all help is appreciated, thanks in advance.

---

### Post by Saint_ on 2009-05-27
**Solved.

installed the alsamixergui and muted Analog loop and Analog loop1.

---

