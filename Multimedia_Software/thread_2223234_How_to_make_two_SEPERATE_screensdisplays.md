---
title: "How to make two SEPERATE screens/displays"
date: 2014-05-10
forum: Multimedia Software
---

### Post by alex199 on 2014-05-10
My GPU has two DVIouts so i have two monitors, but it's being treated as  one logical screen i.e. one DISPLAY :0 and i can drag windows from one  monitor to another. How can i run them like two separate  displays/screens so the windows wouldn't cross from DISPLAY :0.0 to :0.1  in ubuntu 14.04?

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV630 XT [Radeon HD 2600 XT]


```

```
$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: RV630 XT [Radeon HD 2600 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:fe7e0000-fe7effff ioport:b000(size=256) memory:fe7c0000-fe7dffff
```

---

