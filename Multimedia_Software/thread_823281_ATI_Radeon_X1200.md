---
title: "ATI Radeon X1200"
date: 2008-06-09
forum: Multimedia Software
---

### Post by knull on 2008-06-09
i want to enable graphic acceleration my ati card is a Radeon X1200 series, i decided to install the driver from the ubuntu repositories but i have a doubt, does this driver work for my card ?

here is the description from adept manager(kubuntu):

This version of the ATI driver officially supports:
* FireGL: V8650, V8600, V7600, V7350, V7300, V7200, V7100, V5600, V5200, V5100, V5000, HD3870, HD3850, V3600, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p * FireMV: 2200 (Single card PCI-e configuration) * Mobility FireGL: V5000, T2 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, X200, 9800, 9600, 9550, 9500 * Radeon Xpress: 1200 series, 1100 series, 200 series * Radeon: HD2900, HD2600, HD2400, X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500

i cant see my model card listed above. Can this driver work with my ati card?

thank you in advance for attention
sorry for bad english :(

---

### Post by Ptero-4 on 2008-06-09
Maybe it's the Radeon Xpress 1200 series.

---

### Post by knull on 2008-06-09
well, lspci displays the following:


01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]


so i really dont know if it is xpress
...

---

### Post by sim-value on 2008-06-09
X = Xpress ?

---

### Post by Yellow Pasque on 2008-06-09
Yes, the driver will work for RS690 chipsets.
Xpress = integrated (motherboard) graphics

I have an RS690 chip too:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
```

Your English is fine.

---

### Post by knull on 2008-06-09
thank you very much for your help, i appreciate it. About my english i dont use it frequently enough to make myself sure that there will not be some gammatical,lexical or a kind of mistake but thanks for the comment :)


my doubt is solved.

---

### Post by bravo331 on 2008-06-09
I have radeon xpress x1250 in a laptop which is 1200 series chipset; I read in the fourums that this chipset has been "blacklisted" due to a bug that causes Ubuntu to crash if enhanced graphics are enabled

---

