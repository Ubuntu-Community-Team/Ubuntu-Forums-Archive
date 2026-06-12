---
title: "Updating video drivers"
date: 2008-07-20
forum: Multimedia Software
---

### Post by ElliottMarlow on 2008-07-20
I've been trying to run Google Earth but with no luck. When I install and open, all graphics are extremely choppy, and if I try to open the preferences window, it disappears behind all the jumpy graphics. I thought that perhaps my video drivers need to be updated, but I have no idea how to do such. 

I am running Hardy Heron, here is my display info (I think)

        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
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
             capabilities: bus_master cap_list
             configuration: latency=0

Any help is appreciated!

---

### Post by pasyp on 2008-07-24
I had the same problem.It was partly solved by not using the PNP driver, but choosing the LCD driver. But Hardy was unstable on my Acer 3610.
After successful using Gutsy, I had so many problems using Hardy I left it and went back to Gutsy. 
pasyp

---

