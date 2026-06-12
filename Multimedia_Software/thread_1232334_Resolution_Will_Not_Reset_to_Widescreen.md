---
title: "Resolution Will Not Reset to Widescreen"
date: 2009-08-05
forum: Multimedia Software
---

### Post by rodgersmc on 2009-08-05
After plugging an sVideo cord in to hook up my laptop to a tv, the laptop's resolution is stuck on 1024x768, which is a 4:3 ratio.  My laptop is a widescreen and I can't seem to force it to reset and 1024x768 is the highest offered in my display manager.

Any ideas?

---

### Post by rodgersmc on 2009-08-05
If this is helpful:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
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

I do not have any drivers showing up in the driver manager either.

---

