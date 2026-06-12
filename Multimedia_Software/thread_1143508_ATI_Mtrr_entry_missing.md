---
title: "ATI Mtrr entry missing"
date: 2009-04-30
forum: Multimedia Software
---

### Post by moon@K on 2009-04-30
My Laptop has ATI HD3470, and I feel that the graphic performance is little slow.

Compiz can run, all 3D effect can be enabled, looks soomth. I installed Catalyst 9.4. My ubuntu is 9.04. But the output of /proc/Mtrr does not have entry for graphic card. 

I did a fix_mtrr script following the advise from internet. After i boot to shell, the /proc/mtrr now has graphic card memory, but when i boot to graphic mode, the entry for graphic card disappeared.

Even, i first boot to graphic mode, then run script to modify /proc/mtrr, then logout, log in, the entry for graphic card disappeared again.

My question is that, can /proc/mtrr with graphic card memory speed up my computer or not for ubuntu 9.04?
Looks like that xorg removes the entry, is it normal?

When i first boot to shell, modify /proc/mtrr, and then startx, the compute will hang, and i will not be able to switch to terminal by Alt+Ctrl+F1, for F2.

Any suggestions?

---

### Post by moon@K on 2009-04-30
Anyone? Here is my /proc/Mtrr output

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07fe00000 ( 2046MB), size=    2MB, count=1: uncachable

---

