---
title: "Nvidia 8500GT fun"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by Crowie on 2007-06-05
Hi Im currently using kubuntu feisty on 2.6.20-15-generic kernel and having few issues with getting my latest graphics card a PCIe 8500GT working using nvdia proprietry drivers beta version 100.14.06 which I believe are the only version which may support this card.

I was wondering if anyone had this working with either ubuntu or kubuntu feisty as im having no success.  I can install drivers without any issues however just a black screen when i start x.  I appreciate this is a beta driver but interested to see if anyone had any joy.

Kernel picks card up as:

```
lspci | grep -i nvidia
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1)
```

Im on home network so can break it again and ssh in and post any logs output if needed.

My current graphics on this box is an ATI xpress 200 chipset which works fine with ATI driver not sure of the version fglrx but grabbed through the ubuntu repo's.

TIA

---

### Post by Crowie on 2007-06-07
bump ;)

---

### Post by stchman on 2007-06-07
> **Crowie said:**
> Hi Im currently using kubuntu feisty on 2.6.20-15-generic kernel and having few issues with getting my latest graphics card a PCIe 8500GT working using nvdia proprietry drivers beta version 100.14.06 which I believe are the only version which may support this card.

I was wondering if anyone had this working with either ubuntu or kubuntu feisty as im having no success.  I can install drivers without any issues however just a black screen when i start x.  I appreciate this is a beta driver but interested to see if anyone had any joy.

Kernel picks card up as:

```
lspci | grep -i nvidia
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1)
```

Im on home network so can break it again and ssh in and post any logs output if needed.

My current graphics on this box is an ATI xpress 200 chipset which works fine with ATI driver not sure of the version fglrx but grabbed through the ubuntu repo's.

TIA

As of right now Ubuntu has poor support for the 8xxx series of nvidia cards.  I imagine the next kernel in Gutsy will probably support the card.

---

### Post by UKer on 2007-06-07
I've not tried in ubuntu, but on SuSE the driver works very well. Have you set the colour depth to 24bit in your Xorg, and set that up properly? Please provide your Xorg.conf to check.

---

### Post by Crowie on 2007-06-07
yer i fudged about about with xorg.conf I wait for a later kernel.

---

