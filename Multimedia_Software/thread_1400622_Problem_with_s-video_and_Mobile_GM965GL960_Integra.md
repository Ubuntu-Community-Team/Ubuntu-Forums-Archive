---
title: "Problem with s-video and Mobile GM965/GL960 Integrated Graphics Controller"
date: 2010-02-07
forum: Multimedia Software
---

### Post by lee-anna-loo on 2010-02-07
Hi

My friend has Acer notebook with Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller, and we were trying to connect it to the TV using the s-video connector.

He has installed Ubuntu 9.10 [Karmic Koala].

This is what I get from 
> lshw -class display

>  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:fc000000-fc0fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fc100000-fc1fffff


The problem is that we don't get anything by pressing Fn+F5, and nothing cannot be done by using the System->Preferences->Display.

Also it's strange that the file xorg.conf is empty

---

