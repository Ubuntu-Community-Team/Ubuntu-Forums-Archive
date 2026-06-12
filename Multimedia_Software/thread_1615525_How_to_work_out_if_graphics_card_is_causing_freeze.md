---
title: "How to work out if graphics card is causing freezes"
date: 2010-11-07
forum: Multimedia Software
---

### Post by GROwen on 2010-11-07
Hi all,

Not too long ago I changed my graphics card because the fan on an Inno3d Ge-Force 6600 was burnt out. I installed an Inno3d Ge-Force 6200 (PCI Express/AGP 8x 512mb ddr2 is what's labelled on the box) and have since experienced regular complete system freezes when using full screen flash video and mythTV.

I need to run a proprietry drivers because otherwise the flash video is very choppy, I've tried both available (173 and 96) and the freeze occurs with both.

I've put the old card back and everything runs fine.

How would I go about diagnosing the problem to see if it can be fixed? If it can't, how do I find out what card I should be looking to purchase that will be compatible with my motherboards chipset and ubuntu?

Thanks in advance for any help with this.

---

### Post by inobe on 2010-11-07
the model specs doesn't make sense, that is an agp card "only"

[http://www.inno3d.com/products/graphic_card/gf6_agp/6200.htm](http://www.inno3d.com/products/graphic_card/gf6_agp/6200.htm)

you stuck an agp card into a pci-express slot, not good......

[http://www.inno3d.com/products/graphic_card/gf6_pcie/6600.htm](http://www.inno3d.com/products/graphic_card/gf6_pcie/6600.htm)

---

### Post by Yellow Pasque on 2010-11-07
Not sure about freezing. Maybe the card wasn't seated properly. I'm just wondering why you don't replace the fan and/or heatsink on the card that works. That seems a lot cheaper/easier than buying new hardware.

> you stuck an agp card into a pci-express slot, not good......
Where does OP say he has PCIe? It wouldn't fit anyway..

---

### Post by inobe on 2010-11-07
> **Temüjin said:**
> Not sure about freezing. Maybe the card wasn't seated properly. I'm just wondering why you don't replace the fan and/or heatsink on the card that works. That seems a lot cheaper/easier than buying new hardware.


Where does OP say he has PCIe? It wouldn't fit anyway..

you are joking rite ?

is this my brother james, he lives in p.a. too 

:lol:

---

### Post by Yellow Pasque on 2010-11-07
No, what are you talking about?

---

### Post by inobe on 2010-11-07
he downgraded from a PCI-E card to agp, he has an agp card in a pci-e slot.

read the post again.

---

### Post by Yellow Pasque on 2010-11-07
The only thing mentioned about PCIe is something he/she is reading on the box (which also says AGP for some reason).

Anyway, it would still be easier to fix the fan than use a card that doesn't work or buy new hardware.

---

### Post by inobe on 2010-11-07
> **Temüjin said:**
> 
Anyway, it would still be easier to fix the fan than use a card that doesn't work or buy new hardware.

i totally agree, their is no need to replace or downgrade the card, install another fan and be done with it.

---

### Post by GROwen on 2010-11-07
Thanks for the responses guys,

Reason for not just changing the fan was because I'd been told by a rep at my local computer store that it'd be hard to find a replacement for that card. Also, after taking the heatsink off there was a large amount of paste stuck to the chip, just seemed like a lot of work to replace the fan when a new card would be a lot cleaner and simpler and only marginally more expensive than replacing the fan with something like a Zalman...or so I had hoped.

It's definitely an AGP card in an AGP slot, Temüjin is correct in pointing out that in my OP PCI Express/AGP is what's listed on the box, not sure why but not being an expert I thought it worth mentioning in case this could somehow be causing a conflict. Maybe I've been sold a knock-off if it's stating things that aren't possible.

Anyway back to the point, how would I diagnose this concern?

---

### Post by Yellow Pasque on 2010-11-07
Does it use non-standard mounting holes or something? Excess thermal paste is easily removed with rubbing alcohol (google it).

If you had a PCIe slot, buying a cheap replacement would be easier, but it's going to be difficult to find a better AGP card than a 6600.

---

### Post by GROwen on 2010-11-07
Not sure about the mounting holes, here's a [link ]("http://www.hexus.net/content/item.php?item=908&page=2")to a page that has an image of a card with the same cooler. Cooler Master looks like a reputable brand so maybe the mount holes are standardised (are mount holes standardised across the industry?)

When I looked at this Zalman product, [VF700]("http://www.zalman.co.kr/product/cooler/VF700_6600GT_eng.html"), I'd decided it wasn't suitable for my card because my isn't a GT model and the fan would need to sit diagonally to where it's designed to fit. So I think I'm out of luck with a third party option, unless there's other options you'd be able to point me towards.

Also, what log files should I be looking at to see what errors have occured when the system has crashed?

---

