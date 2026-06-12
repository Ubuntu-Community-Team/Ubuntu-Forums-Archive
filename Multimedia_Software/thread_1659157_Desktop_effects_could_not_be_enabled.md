---
title: "Desktop effects could not be enabled"
date: 2011-01-03
forum: Multimedia Software
---

### Post by cookie6 on 2011-01-03
Hello, when I installed Docky, it said it needs compositing to work. So I go to the appearance then visual effects. But when I click Normal, it says it can't enable it. :confused: (look at screen shots) I just installed Ubuntu 10.04 on this computer, its Comoaq Evo. Also, I did check and update Ubuntu.
 [ATTACH]180035[/ATTACH][ATTACH]180036[/ATTACH]

---

### Post by mikewhatever on 2011-01-03
Some graphics cards can't handle desktop effect, in which case, they are disabled. If you have, for example, an older Intel graphical accelerator, there isn't much to do, other then pray that Intel fixes the driver. Chances are slim though.

---

### Post by cookie6 on 2011-01-03
> **mikewhatever said:**
> Some graphics cards can't handle desktop effect, in which case, they are disabled. If you have, for example, an older Intel graphical accelerator, there isn't much to do, other then pray that Intel fixes the driver. Chances are slim though.

How do I know if I have the right driver installed? Or any driver installed? Because I have no idea what video card I have.

---

### Post by mikewhatever on 2011-01-03
You must have a driver installed, because otherwise, there wouldn't be any graphical output. You can find out more about the hardware you use with Hardinfo, a handy program from the Software Center. To just check the graphics, run **sudo lshw -C display** in a terminal.

---

### Post by cookie6 on 2011-01-03
> **mikewhatever said:**
> You must have a driver installed, because otherwise, there wouldn't be any graphical output. You can find out more about the hardware you use with Hardinfo, a handy program from the Software Center. To just check the graphics, run **sudo lshw -C display** in a terminal.

I did the code, and this is the results: 
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff(prefetchable) memory:fc400000-fc47ffff

---

### Post by mikewhatever on 2011-01-03
Desktop effects are disabled with Intel's 8xx graphics because of xserver crashes.

---

