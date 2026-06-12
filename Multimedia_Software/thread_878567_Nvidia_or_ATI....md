---
title: "Nvidia or ATI...?"
date: 2008-08-03
forum: Multimedia Software
---

### Post by Prodromoi on 2008-08-03
Logged on this morning and... one completely blank screen on my dual-monitor setup.  Not even the BIOS page was being displayed!  I'm still running through all the possibilities but I think that it's the graphics card (or at least the CRT output side of it) that's failed, rather than the monitor.

So I'm probably going to be looking for a new graphics card soon.  (The current one is a Nvidia 7300LE PCI-E).

What's the prevailing opinion at the moment about which graphics cards are the best option?

The relevant details of my system are:
64-bit Ubuntu 8.x
PCI-E graphics card slot
Needs to run a CRT and an LCD display
I'm not a computer gamer so while a fast card is nice, it doesn't need to be cutting edge (ideally a maximum budget of approximately £50 GBP)
I don't want/need TV or HDTV capabilities on the card

Thanks in advance.
A

---

### Post by Vakman on 2008-08-03
I strongly suggest nVIDIA. I will never buy ATI cards again.

---

### Post by noobuntu35 on 2008-08-03
> **Prodromoi said:**
> Logged on this morning and... one completely blank screen on my dual-monitor setup.  Not even the BIOS page was being displayed!  I'm still running through all the possibilities but I think that it's the graphics card (or at least the CRT output side of it) that's failed, rather than the monitor.

So I'm probably going to be looking for a new graphics card soon.  (The current one is a Nvidia 7300LE PCI-E).

What's the prevailing opinion at the moment about which graphics cards are the best option?

The relevant details of my system are:
64-bit Ubuntu 8.x
PCI-E graphics card slot
Needs to run a CRT and an LCD display
I'm not a computer gamer so while a fast card is nice, it doesn't need to be cutting edge (ideally a maximum budget of approximately £50 GBP)
I don't want/need TV or HDTV capabilities on the card

Thanks in advance.
A
Have you eliminated that it's anything but the Card? I.E have you tried another monitor? if you have narrowed it down to _Its the card_ the Nvidia cards work fine with Ubuntu I have a GeForce 8600 Pci-E and Using a DELL monitor... but the Drivers are not produced by Nvidia. where as the SLI cards are.

---

### Post by Prodromoi on 2008-08-03
> **Thisislaw said:**
> I strongly suggest nVIDIA. I will never buy ATI cards again.
For any particular reason?

---

### Post by Vakman on 2008-08-03
> **Prodromoi said:**
> For any particular reason?
Sorry, I kind of just posted and then had to eat :)
Yes, I have found that when I had a nVIDIA card, Geforce 7300 I believe it was, the drivers for it worked well and I had few to no issues. nVIDIA is known to have better support for Linux where as ATI, AMD now I guess, is improving but I still find not up to nVIDIA. If you look for discussions about nVIDIA vs ATI, in most it will suggest nVIDIA as well. Though I have seen sites that suggest ATI cards, I personally find nVIDIA cards to be better for myself and usually others as well.
Also to the poster and others, [http://ubuntuforums.org/showthread.php?t=867948](http://ubuntuforums.org/showthread.php?t=867948) this thread talks about which card to choose. Someone is asking the same question basically.

---

### Post by eye208 on 2008-08-03
Currently the choice between Nvidia and ATI is a tough one. It's true that Nvidia's drivers perform better at the moment, but ATI is the vendor that has disclosed its GPU specifications. This means there will be an accelerated 3D capable ATI driver available as open source and licensed under the GPL. This driver will certainly become a part of the Linux kernel source tree sooner or later. At this point ATI cards will become the #1 choice for Linux, unless Nvidia decides to follow suit.

I'm using Nvidia now, but when the open source ATI driver has matured I will definitely switch to ATI.

---

### Post by ykcirt on 2008-08-03
Ah, I just wanted to say that I've been following this discussion with interest. I have an Ati 9800xt and tried Gentoo, Fedora 9 and now finally Ubuntu (which I'm sticking with). Drivers are meh, I can't use WINE very well. I suppose Tuxracer had no problems.

I think I'm going to try to find Nvidia's hardware equivalent of my old 9800xt, which will probably be a Geforce 6800GT or a 7600GT. 

It's a sad state of affairs, but at least I'll be paying a fraction of the original price. I'd buy an all new superfast generation GPU, but I'm afraid my five year old computer won't be able to handle that.

> **eye208 said:**
> Currently the choice between Nvidia and ATI is a tough one. It's true that Nvidia's drivers perform better at the moment, but ATI is the vendor that has disclosed its GPU specifications. This means there will be an accelerated 3D capable ATI driver available as open source and licensed under the GPL. This driver will certainly become a part of the Linux kernel source tree sooner or later. At this point ATI cards will become the #1 choice for Linux, unless Nvidia decides to follow suit.

I'm using Nvidia now, but when the open source ATI driver has matured I will definitely switch to ATI.

Hmm, that's interesting though. Got any idea how long I would have to wait for that to happen? Or which site I need to keep tabs on to follow the development?

---

### Post by Vakman on 2008-08-03
> **ykcirt said:**
>  Drivers are meh, I can't use WINE very well. Got any idea how long I would have to wait for that to happen? Or which site I need to keep tabs on to follow the development?
Can't use Wine very well. And I also wonder about that site to follow the development. I know of [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) (Radeon driver) but that is the only site I know of.
In a thread that I posted ([http://ubuntuforums.org/showthread.php?t=869158](http://ubuntuforums.org/showthread.php?t=869158)), it has to do with Guild Wars under Wine with my ATI card. Here is a quote from the most recent poster.
> **Ferrat said:**
> Ati drivers have some problems with GW, I'm using nVIDIA and GW works out of the box for me with WINE at a steady 50+ FPS
This seems like a good enough reason for myself to get a nVIDIA card again, if I had the money. Point being, I will pick nVIDIA over ATI any day so long as the drivers are better. I will try to keep both I suppose. As eye208 said ATI driver will mature, time will tell I guess.

---

### Post by ykcirt on 2008-08-04
I found this page here:
[http://xorg.freedesktop.org/wiki/RadeonFeature](http://xorg.freedesktop.org/wiki/RadeonFeature)

That's the driver, right?

I have an r300 generation card. It might already be worth my time trying this driver out.

---

### Post by revolutio on 2008-08-04
Wait for DRI2.  Until then ATI cards are kinda worthless in Ubuntu and handle 3D features like a wombat handles an Escalade.  As for when DRI2 is implemented...

I'm all for open-source, but if I'm given a choice between closed-source and functional and open-source but broken I'll stick with the former.

Bottom line: If you prefer Linux and need a new video card now, go with Nvidia.

---

