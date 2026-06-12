---
title: "Maybe this is the reason of mtrr allocation  problem ?"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by ilans on 2005-10-21
I run:
 cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1

I have only 512 MB of ram in my PC so why I get this wrong value?
In addition I don't get reg01 & reg02 values .

Maybe this wrong number is the reason to my mtrr allocation error  (that lead to
lack of 3D acceleration on my Radeon 9550 card)???

Any way:
how can I force the system to recognize the right amount of ram ?

---

### Post by schlika on 2005-11-17
Hi there ...

I have the same trouble here :

I865 chipset, 1Gb ram, AGP Radeon 9700, cat /proc/mtrr gives me :

reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=1

I remember having a much more complete answer when using other kernels / distrib ...

Could someone help ?

---

