---
title: "New card, chicken-and-egg problem"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by Tryke on 2005-12-08
(long-time lurker, first-time poster, hello all)

My 5-year-old 3com NIC finally died a valiant death last week. To replace it, I've picked up a fresh new D-Link DFE-530TX+ (the model number is probably irrelevant at this point).

To my surprise, the driver CD actually had Linux drivers on the disc. Unfortunately, they were source drivers that needed to be compiled against the kernel, and I did not have the kernel-source downloaded to my computer. I can access the Internet from my Windows partition, but I would much rather spend my time in Linux again. :) 

My question is two-fold: Is it possible to use my Windows installation to download my kernel source from an APT repository, so that I may copy it over to the linux partition and install it? Failing that, is there anything on the Ubuntu CD that can help me? I would have already checked the CD, but I would need to download a new one, and I'd rather download just the kernel source if possible.

I would much rather leave re-installing Ubuntu as a very last resort. I do have /home on a separate partition (a habit that has saved me in the past), but I don't know if I could remember all the programs and tweaks I've installed.

---

### Post by Digitallysick on 2005-12-08
have you went here? [http://ubuntuguide.org/](http://ubuntuguide.org/) i have mine setup where in linux, i can see my windows partition, and copy the files over if needed, this is great, so if you dont have it setup this way, might be the best, then you can go in windows download whatever, boot into linux and copy it over, (or you could use a jumpdrive ) either or.

---

### Post by Tryke on 2005-12-08
I certainly have my computer set up to copy files from my Windows partition to my Linux partition. My problem lies in finding this "whatever" you speak of. ;)

UPDATE: I've found a Kubuntu LiveCD kicking around a desk drawer. I've just booted from it, time to poke around and see if there's any way to move drivers to my already-installed Ubuntu...

---

### Post by VenomousGecko on 2005-12-08
I am not 100% sure of this, but seeing as how the hardware detection and kernel that is shipped with Ubuntu seems to have all of the modules needed you should be able to just plug the card in, boot, and be on your way.  The module used by this card should be the rtl8139 module which is part of the kernel.

---

### Post by Tryke on 2005-12-08
Well, I'll be. I was certain the card did not work the first time I booted into Linux with it. But this time, it was autodetected. I suppose I didn't have a problem after all :???: ... thanks for the quick replies, anyway. :)

---

