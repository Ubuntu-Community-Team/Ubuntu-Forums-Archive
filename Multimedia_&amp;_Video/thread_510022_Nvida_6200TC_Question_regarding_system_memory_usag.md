---
title: "Nvida 6200TC Question regarding system memory usage"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by smartbei on 2007-07-26
The 6200TC has 64mb of onboard memory. My question is whether Ubuntu automatically sees that the card is a TC (as in, it is meant to take a part of the system memory). If yes, how can I verify this? If no, where can I set it so that it does?

I seem to recall that one of the screens when running sudo dpkg-reconfigure xserver-xorg has to do with a graphics card's usage of system memory. Is this it?

I have 1GB of system memory. Would allocating memory to the graphics card improve performance during games? In other words, would there be a noticeable difference in performance if the graphics card's usage of system memory was 64mb? 128mb?

Thanks for all responses!

---

### Post by ddrichardson on 2007-07-26
Graphics card memory is controlled at the BIOS level - not the OS. In BIOS there is a setting, something along the lines of AGP aperture size that lets you configure the memory setting.

The setting in Xorg does correspond to the installed available memory on your card.

I think you're confusing shared and on board memory as AFAIK there are no cards that can combine system and dedicated RAM.

---

### Post by smartbei on 2007-07-26
See [http://www.pcstats.com/articleview.cfm?articleID=1805](http://www.pcstats.com/articleview.cfm?articleID=1805). This is nearly the same as the card I have. Mine has 64mb onboard. From what I understand from that article, the card both has onboard and is able to access system memory at need.

Besides, the card is PCI-E, not AGP, so I am not sure what is meant by 'AGP aperature size'.

---

### Post by ddrichardson on 2007-07-26
I did say *something* like agp aperture size - if you know its pci then its likely to be PCI aperture size!

Reading through [nVidia's TurboCache site]("http://www.nvidia.com/page/turbocache") it doesn't give much information on how this usage of system memory is achieved - whether its controlled in hardware or by the driver itself. However as this is one of the cards supplied in Dell Ubuntu laptops there may be a way.

Reading through their site though it does elude to this being a DirectX thing and in any case something must be controlling the memory allocation because it isn't allocating a set amount of shared RAM it's allocating it on the fly as its needed. It may be worth contacting nVidia or posting on thier forum to see if the latest nVidia Linux drivers support TurboCache.

---

### Post by smartbei on 2007-07-26
Searched the NVidia knowledge base and found this: [http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=805](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=805). Apparently its 'Graphics Aperature Size', but it still only applies to AGP cards.

Thanks for the idea to post in their forums - here is the link: [http://forums.nvidia.com/index.php?showtopic=41672](http://forums.nvidia.com/index.php?showtopic=41672)

---

