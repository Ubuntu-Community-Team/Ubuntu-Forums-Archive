---
title: "Change out ATI Radeon 7000 for a Nvidia Geforce 6200?"
date: 2009-05-16
forum: Multimedia Software
---

### Post by bstanley on 2009-05-16
Hi!
I am currently having lots of problems with compiz locking up the system.
I am using Ubuntu 9.04.

I am using an ABIT KT7A Mother board with an ATI Radeon 7000/VE Rv100qy
Viedo card.  The driver being used is the open source  radeonfb driver.

After looking at several post on this site with people having problem with
new and older ATI cards I am thinking about changing to a nvidia card.

With this older  AGP 4X motherboard, I don't have to many selections to 
choose from.

I am thinking about switching to the  Geforce 6200 card by Jaton.

Do the current drivers from nvidia support this card?

Does anyone know if this card will work well with an AGP 4X board and with
compiz 3D effects?

---

### Post by bstanley on 2009-05-16
Does anyone have any information on compiz and a Geforce 6200 Card?

---

### Post by urosg3 on 2009-05-16
I have that card and work fine. I don't have any problems installing driver and compiz running fast. Very god supported card.

Cheers

---

### Post by mattwilkes512 on 2009-06-26
> **urosg3 said:**
> I have that card and work fine. I don't have any problems installing driver and compiz running fast. Very god supported card.

Cheers

What driver are you using for your 6200 card?  There is a forum with PPAs for the 185.xx and 190.xx series drivers which I think would work for this card.  Does Ubuntu recognize it and recommend the 180 driver in Jockey?  Also what version of Ubuntu are you running? And is your card PCI or PCIe?

thanks

---

### Post by Bucky Ball on 2009-06-26
Generally, it will recognise the card and inform you there are restricted, third-party drivers available for the device and ask if you want to use them. It is a fairly 'follow your nose' procedure usually with Nvidia nowadays, although problems occasionally arise. There are ways around that too, like Envy, available in Synaptic Package Manager, which will attempt to ID your card, uninstall any wrong drivers and install the correct one (also works with ATI apparently).

I wouldn't panic too much about working out which driver you should be using until you actually put the vid card in and see what happens. It is not exactly what you're going through at this point (probably). They are better supported.

---

### Post by mattwilkes512 on 2009-06-26
> **Bucky Ball said:**
> Generally, it will recognise the card and inform you there are restricted, third-party drivers available for the device and ask if you want to use them. It is a fairly 'follow your nose' procedure usually with Nvidia nowadays, although problems occasionally arise. There are ways around that too, like Envy, available in Synaptic Package Manager, which will attempt to ID your card, uninstall any wrong drivers and install the correct one (also works with ATI apparently).

I wouldn't panic too much about working out which driver you should be using until you actually put the vid card in and see what happens. It is not exactly what you're going through at this point (probably). They are better supported.

I already had a PNY PCI 512mb nvidia 8400gs card and tried to install it on my dell dimension 2400 that has onboard graphics.  A fresh Ubuntu 9.04 install recognized the card and recommended driver 180; but when I installed 180 the card did not work.  I only mention this other card because it uses the same recommended driver-according to nvidia.  My BIOS has only onboard and auto features for graphics, and was set to auto, so I dont think theres anything I could have done differently there.  So do I need 185.xx or 190.xx to run a 8600gs?  What about the 6200?  I have since returned the 8600gs card but am considering a repurchase, or the 6200, as I just found the forum for nvidia 180+.

---

### Post by GCFreak on 2009-06-26
Always disable onboard hardware that you're not using, as they can and probably will cause issues with hardware detection and operation.

---

### Post by Bucky Ball on 2009-06-27
Try to get Envy to install it for you. It is in the repositories (Synaptic). You can choose which driver. The good thing is, it will REMOVE, or try to, any incorrect driver you have installed or installed wrongly.

---

### Post by mattwilkes512 on 2009-06-27
> **Bucky Ball said:**
> Try to get Envy to install it for you. It is in the repositories (Synaptic). You can choose which driver. The good thing is, it will REMOVE, or try to, any incorrect driver you have installed or installed wrongly.

Originally after no luck with the 180 driver from jockey I did try Envy.  It suggested the same driver and installed it with the same result-unable to run compiz?  I'm going to try the 185.xx and/or 190.xx but am not sure what to do if that doesnt work.

---

