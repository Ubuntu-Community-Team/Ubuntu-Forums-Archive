---
title: "PCI-E x8 Video Card"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by punkle on 2008-01-31
Hi,

I am considering a new Video Card, and am relatively new to Ubuntu so I have a few questions that I hope someone will be able to help me with.

Do I need to buy a Video card or type of video card that is supported by Ubuntu/Linux?

Is there such thing as a PCI-E x8 Video Card? I have browsed the internet and not had much luck finding one. 

I did find someone mentioning that there was a was a way that you can plug a x16 into a x8 slot. Does anyone know anything about this? Do you need additional hardware/software, is it supported by Linux etc.

I apologise for the ignorence, Any help is greatly appreciated.

---

### Post by theacoustician on 2008-01-31
Why are you looking for a x8 card in the first place?  x16 is rather standard for video.

---

### Post by Ptero-4 on 2008-01-31
For brands of GPUs go with NVidia, you can't go wrong on that, and avoid ATI like the plague. Their drivers are crappy as hell.

---

### Post by punkle on 2008-01-31
> **theacoustician said:**
> Why are you looking for a x8 card in the first place?  x16 is rather standard for video.

My computer only has 3 x8 and 1 x1 pcie ports.

---

### Post by shad0w_walker on 2008-01-31
Unless I have a gross misunderstanding of PCI-E then a higher speed card (16x) will simply lower its speed to match the maximum the socket can handle, like SATA, USB, etc.

---

### Post by lestatxxx on 2008-01-31
> **Ptero-4 said:**
> For brands of GPUs go with NVidia, you can't go wrong on that, and avoid ATI like the plague. Their drivers are crappy as hell.

Tell me about it, I can't wait to save enough money to fully upgrade my p5b motherboard and install a Sli 8800GTx and get rid of this ati card ><...

I have a radeon 9800 and a 9200, using 9200 since 9800 isn't compatible with ECS-865 M7 v2 Mobo ><...

---

### Post by Squish on 2008-01-31
by x8, you dont mean AGP then do you? PCI and AGP are differant. 

I would suggest a 7000 card series, seeing how you wont need dx10 technology any time soon, and considering your bottle neck. XFX dominated that era, so if you can find one at a good price...

---

### Post by Yellow Pasque on 2008-01-31
When you say your slots are x8, does that mean they're physically smaller than normal x16 slots or just that they don't run at full speed? If it's the latter, then an x16 card will work normally (just at lower bandwidth, which probably won't cause much performance loss). If it's the former, then you'll need to look for x1 video cards as I'm not aware of x4 or x8 cards.

What mobo do you have?

---

### Post by _Phineas_ on 2008-01-31
[http://www.thenerds.net/HEWLETTPACKARD.HP_HP_x4x8_PCIE_Bus_Expander_Option_Kit_1_x_PCI_Express_x8.403724B21.html?affid=8&ci_src=14110944&ci_sku=403724B21%5E~%5EHEWLETT-PACKARD#reviews](http://www.thenerds.net/HEWLETTPACKARD.HP_HP_x4x8_PCIE_Bus_Expander_Option_Kit_1_x_PCI_Express_x8.403724B21.html?affid=8&ci_src=14110944&ci_sku=403724B21%5E~%5EHEWLETT-PACKARD#reviews) this is a pci-e x8 card the only one I could find. Good luck! :popcorn:

---

### Post by punkle on 2008-02-01
I found this thread on the Nvidia forum relating to this : [http://forums.nvidia.com/index.php?showtopic=38981](http://forums.nvidia.com/index.php?showtopic=38981)

---

### Post by theacoustician on 2008-02-01
> **punkle said:**
> My computer only has 3 x8 and 1 x1 pcie ports.
WTF?  Mind if I ask what motherboard you're using?  I've NEVER seen such a thing in a consumer board and can't even recall seeing a server board like that.

---

### Post by theacoustician on 2008-02-01
> **shad0w_walker said:**
> Unless I have a gross misunderstanding of PCI-E then a higher speed card (16x) will simply lower its speed to match the maximum the socket can handle, like SATA, USB, etc.
Assuming the socket is the right size.  If you had a x16 socket electrically wired for only x8, you're absolutely correct.  You can't shove a x16 card in a x1 slot though.  I suppose you could dremel out the blocking bits of plastic and and in theory it should work, but I can't imagine the card would be seated very well and that might lead to problems.

---

### Post by punkle on 2008-02-01
> **theacoustician said:**
> WTF?  Mind if I ask what motherboard you're using?  I've NEVER seen such a thing in a consumer board and can't even recall seeing a server board like that.

Its a Dell PowerEdge T105, I don't know what Motherboard it is. It is a server computer.

---

### Post by theacoustician on 2008-02-01
> **punkle said:**
> Its a Dell PowerEdge T105, I don't know what Motherboard it is. It is a server computer.
Good news!

I looked at the documentation for your computer on Dell's website.  Straight from the manual ([http://support.dell.com/support/edocs/systems/pet105/en/HOM/PDF/JN5510MR.pdf):](http://support.dell.com/support/edocs/systems/pet105/en/HOM/PDF/JN5510MR.pdf):)
> NOTE: The size of the expansion card connectors for the PCI x8 card is PCI x16.
So you should be able to buy any x16 card and have it work perfectly.  You won't get quite the same performance out of it as you might a full x16 lane, but it'll do.

Also of some interest, you only have (2) x8 PCIe slots.  The third slot is regular old PCI.  That means if all else fails, you could buy an old PCI video card.

Good luck!

---

### Post by punkle on 2008-02-01
Cheers, Thats brilliant.

---

