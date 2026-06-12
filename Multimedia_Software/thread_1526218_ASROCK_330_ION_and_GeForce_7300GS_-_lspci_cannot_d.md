---
title: "ASROCK 330 ION and GeForce 7300GS - lspci cannot detect both"
date: 2010-07-07
forum: Multimedia Software
---

### Post by fi2 on 2010-07-07
I installed a secondary Nvidia GeForce7300GS 256 PCIe video card in an ASROCK ION 330 motherboard. The idea is to provide an S-video output. 

The interesting bit is that lspci shows only one of the two cards. If I set the ION video adaptor primary in BIOS, then lspci will detect only ION, if I set the PCIe video card then lspci will detect the GeForce 7300GS. I'd like to write my own xorg.conf, but how can I refer to drivers without the pci bus address?

Any help would be highly appreciated.

---

### Post by fi2 on 2010-07-09
No idea...?

---

### Post by SunnyBUG on 2010-07-29
Same with Asus P5B mother board.

If I set integrated primary - lspci will see only integrated card.
Setting PCIe as primary will make lspci see only PCIe card.

---

### Post by fi2 on 2012-02-11
Long time, and nearly forgotten it, but recently I tried lspci and it works like charm. 

In the meantime I installed Oneiric on the ASROCK - it may be the new kernel.

---

