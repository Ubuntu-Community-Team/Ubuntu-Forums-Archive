---
title: "nvidia video cards for an older PC"
date: 2011-01-27
forum: Mythbuntu
---

### Post by boondocks on 2011-01-27
This is an older spare PC that has 2 GB of RAM.
According to the specifications it has:
[LIST]
[*]one **PCIe x8** slot, 2.5-GHz, 3.3-V, 12-V
[*]one **PCIe x1** slot, 2.5-GHz, 3.3-V, 12-V
[/LIST]
In order to get the most out of VDPAU in Mythbuntu ...
Are there any nvidia cards that are known to work in any of these PCIe slots?

---

### Post by Joe of loath on 2011-01-27
Pretty much any PCI-E graphics card will work in there. Just buy an nVidia card that fits your budget and it will work. For a mythbuntu front end fanless might be a good idea, too.

---

### Post by boondocks on 2011-01-27
> **Joe of loath said:**
> Pretty much any PCI-E graphics card will work in there. Just buy an nVidia card that fits your budget and it will work. For a mythbuntu front end fanless might be a good idea, too.

Are PCI-E cards better at handling HD video?
Compared to the regular PCI cards.

---

### Post by Joe of loath on 2011-01-27
PCI cards are very old, you won't find the same kind of performance from PCI as you would PCI-E.

---

### Post by LowSky on 2011-01-27
> **boondocks said:**
> Are PCI-E cards better at handling HD video?
Compared to the regular PCI cards.

pci hasnt really been used for graphic in a long time. agp was the standard before pcie. and yes pcie are much better.

---

### Post by newlinux on 2011-01-27
> **boondocks said:**
> Are PCI-E cards better at handling HD video?
Compared to the regular PCI cards.

the PCI bus doesn't have enough bandwidth for good graphics by itself - not even for HD decoding - that's what brought AGP along. All decoding for HD broadcasts with a PCI card would have to be in hardware on the GPU - meaning VDPAU (there actually are a few PCI 8400GS cards that are VDPAU capable). That being said, PCIe is defintely the current standard now and most video cards will be PCIe. Make sure you get a VDPAU capable card.

Keep in mind a PCIe x16 card will not fit in a PCIe x8 or x4 or x1 slot (without hardware modification), but a PCIe x1 or x4 or x8 will fit in a PCIe x16 slot (smaller can fit in larger)

That will make finding a video card more difficult. The only one I saw on newegg that will work in x1 slot is:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500164](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500164)

---

### Post by boondocks on 2011-01-28
> **newlinux said:**
> 
...
PCIe is defintely the current standard now and most video cards will be PCIe. Make sure you get a VDPAU capable card.
...
That will make finding a video card more difficult. The only one I saw on newegg that will work in x1 slot is:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500164](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500164)

Hey newlinux, Thanks for this link!
I purchased this "ZOTAC ION-GPU-A-E ION Graphics Processor 512MB DDR3 PCI Express x1 HDCP Ready Low Profile Ready Video Card".
Popped it into my Mythbuntu system and it is up and running.
With VDPAU enabled, the HD looks great.
Before I used this card, with HD the CPU was at 100% and HD was unwatchable.
After I installed this card, with HD the CPU is below 45% and HD is just fine.

---

