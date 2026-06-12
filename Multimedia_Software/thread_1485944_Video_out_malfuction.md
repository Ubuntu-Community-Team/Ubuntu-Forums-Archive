---
title: "Video out malfuction"
date: 2010-05-17
forum: Multimedia Software
---

### Post by conradin on 2010-05-17
Ok, This is a strange problem Ive been encountering with the 2.6.32.22 kernel. That, videos, be them avi, flv, or anything else, appear both pixelated and only in the colours Red, Green, Blue, and black. 

The sound quality is fine, only video seems to have some malfunction. 
when I stepped back a few kernel releases, everything worked fine. 

Does anyone else have this problem?

Below is my lshw for my video Card
```

*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:90080000-900fffff ioport:1800(size=8) memory:b0000000-bfffffff(prefetchable) memory:90000000-9003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:80200000-8027ffff

```

---

### Post by conradin on 2010-05-20
Bump ?

---

### Post by xc3RnbFO8P on 2010-05-20
In Movie Player (Totem), 
Edit> Preferences> Display, Reset to Defaults

---

### Post by conradin on 2010-05-23
HEY!! IT worked!! Thank You!!!

---

