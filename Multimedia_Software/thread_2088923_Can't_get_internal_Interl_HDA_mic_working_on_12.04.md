---
title: "Can't get internal Interl HDA mic working on 12.04"
date: 2012-11-27
forum: Multimedia Software
---

### Post by afd on 2012-11-27
Full disclosure - I'm actually trying to do this on elementaryOS Luna (beta) but it is based on 12.04 and I have tried the same in 12.04 from liveUSB with the same results (aka no joy).

So I have a Dell Adamo 13 with Intel HDA sound card. The internal mic isn't working after install / liveUSB boot and no amount of fiddling with alsamixer in terminal or installing DKMS from .deb has fixed it.

From sudo lshw:

```
    *-multimedia
         description: Audio device
         product: 82801I (ICH9 Family) HD Audio Controller
         vendor: Intel Corporation
         physical id: 1b
         bus info: pci@0000:00:1b.0
         version: 03
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=HDA Intel latency=0
         resources: irq:46 memory:f8600000-f8603fff
```

From cat /proc/asound/card0/codec* | grep Codec :

```
    Codec: IDT 92HD73C1X5
          Codec: Intel Cantiga HDMI 
```

Any help appreciated. Ubuntu & elementary IRCs came up blank.

---

