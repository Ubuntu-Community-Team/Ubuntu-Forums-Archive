---
title: "I have no sound on HP Pavilion Laptop - HELP"
date: 2009-08-25
forum: Multimedia Software
---

### Post by WhiteSphinx on 2009-08-25
I have no sound:
HP Pavilion DV7-1285DX
Ubuntu 9.04

lshw
...
*-multimedia
     description: Audio device
     product: 82801I (ICH9 Family) HD Audio Controller
     vendor: Intel Corporation
     physical id: 1c
     bus info: pci@0000:00:1c.0
     version: 03
     width: 64 bits
     clock: 33MHz
     capabilities: bus_master cap_list
     configuration: driver=HDA latency=0 module=snd_hda_intel
...


Never mind, I found the answer here: [http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)

and then you have to run alsamixer and bring all the levels up.

---

