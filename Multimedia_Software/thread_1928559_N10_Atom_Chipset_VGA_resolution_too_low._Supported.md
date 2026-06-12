---
title: "N10 Atom Chipset VGA resolution too low. Supported higher res?"
date: 2012-02-20
forum: Multimedia Software
---

### Post by Davidm71 on 2012-02-20
Hi,

I have a Foxconn NT525 Intel Atom N10 chipset netbox and I installed 11.10 and can't get the resolution higher than 1024x800 even though the monitor supports 1600x1200. Anyone know how to get higher resolution?

Thank you.

---

### Post by Davidm71 on 2012-02-20
*-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fee80000-feefffff ioport:cc00(size=8) memory:80000000-8fffffff memory:fef00000-feffffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:ff200000-ff27ffff

---

