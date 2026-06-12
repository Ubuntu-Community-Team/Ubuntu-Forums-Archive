---
title: "Some images distorted"
date: 2012-07-20
forum: Multimedia Software
---

### Post by mobitinker on 2012-07-20
New install on Dell Optiplex GX520. Graphics card detect is Intel 82945G. All is working except the Dash icons (at upper left of desktop) have distorted flyout text balloons. In addition, the images on some web pages are distorted in a pixelated like fashion. See attached. From browsing this forum it looks like the driver I have should do the trick but...  I'm new to Ubuntu too. Sorry if I'm not using right terms yet!

PCI (sysfs)  
  *-display:0             
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:feb00000-feb7ffff ioport:e898(size=8) memory:e0000000-efffffff memory:feac0000-feafffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:feb80000-febfffff

---

### Post by trpped on 2012-09-24
I am having the same problem on a Optiplex 520 and 280

---

