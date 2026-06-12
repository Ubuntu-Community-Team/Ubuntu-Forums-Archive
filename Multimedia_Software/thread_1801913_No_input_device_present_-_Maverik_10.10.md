---
title: "No input device present - Maverik 10.10"
date: 2011-07-11
forum: Multimedia Software
---

### Post by zarnivop2 on 2011-07-11
Hello
I can't use my line-in/microphone jack. In system-management-sound input tab there is no input device listed, and the input controls are grayed-out.
sudo lshw -C sound produced: 
[FONT="Courier New"]description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:43 memory:dfdf8000-dfdfbfff
[/FONT]

BTW totall noob here, pls have mercy.

---

### Post by zarnivop2 on 2011-07-11
SOLVED

Had to change in system-preferances-sound, tab DEVICE, from "analog output" to "analog duplex", then in tab INPUT select **microphone 1**:P

---

