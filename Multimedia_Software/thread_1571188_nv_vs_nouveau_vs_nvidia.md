---
title: "nv vs nouveau vs nvidia"
date: 2010-09-09
forum: Multimedia Software
---

### Post by formaldehyde_spoon on 2010-09-09
I have a GeForce GT 240 running two screen and want to add a Geforce FX 5200 to run a third screen.

Looks like I lucked out with my choice of second card though (didn't have much choice, it had to be vanilla PCI) because the GT240 and FX5200 use incompatible nvidia drivers!  So I need two separate drivers installed to run the two cards...

As far as I know it's impossible to install two versions of the nvidia driver at the same time, and nouveau can't be installed at the same time as nvidia, so that left me with just nv as an option.

Not having much luck with it though, because it seems nv and nouveau are more than just closely related: when using nv, lshw says I'm actually using noveau ??? :confused:
I think that's why I haven't been able to get nv working alongside nvidia - nv/nouveau is removing the nvidia driver....

nv isn't exactly the same as noveau though: when I tried nv for both cards it actually managed to activate all three screens (no other driver/combination of drivers managed to do that) although they only showed a black screen.
nouveau on both cards just failed completely.
When I uninstalled nouveau through synaptic and tried nv on both cards again it failed too, didn't get the three active screens this time :(

So I'm wondering what the relationship between nv and nouveau is?  Can I use nv without nouveau?
I saw some guy somewhere write that he successfully used nvidia and nv drivers alongside each other for two cards - has anyone had any experience in this, or read anything about it?

---

### Post by Yellow Pasque on 2010-09-09
> So I'm wondering what the relationship between nv and nouveau is?
Maybe this will explain a bit better: [http://www.phoronix.com/scan.php?page=news_item&px=ODQ2MQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ2MQ)

---

### Post by formaldehyde_spoon on 2010-09-10
Not a whole lot, but I appreciate the reply! ;)

Thanks to a link within your link, I know know that nv and nouveau aren't related, so lshw telling me I'm using nouveau when I've specified nv in xorg.conf must be for some other reason: is nouveau used by default when there are no nvidia drivers?

But I *do* see different bevaviour between specifying nv and nouveau drivers, so nouveau isn't just simply being swapped in for nv...

Where can I get more info on nv?  Are there howtos somewhere?  
Can I ensure nouveau isn't used?  I've already uninstalled it through synaptic.

---

### Post by hsoulen on 2010-09-10
Hi,

What you are asking is just not going to be possible.

You are stuck in a "catch-22.

Best bet if you really need the support for three displays is to get another card in your series (GT 220/240) or at the very least an 8000/9000 series card.

I know this sucks but even when the Nouveau driver becomes more mature you can guarantee the developers will be attempting support for newer products rather than older ones, same applies for the Nvidia driver team.

If you think this is bad, well at least Nvidia supplies a current 173 series driver for Linux, AMD/ATI has basically left users of older products hanging in the breeze.

Sorry if this is not the answer you are looking for, but honestly that FX 5200 is just not worth the trouble.

Hank

---

### Post by formaldehyde_spoon on 2010-09-10
Ah well, I guess I'll give up on the FX 5200, and buy a 9300 GS (there aren't many choices when it comes to vanilla PCI).  Hopefully I can get my money back for the 5200! ;) 

Thanks for the input guys, much appreciated.

---

### Post by Yellow Pasque on 2010-09-11
> **formaldehyde_spoon said:**
>   Hopefully I can get my money back for the 5200!
If you can't and you're in the U.S.A., send me a PM and let me know how much you want for it. I have a P3-900/intel 815e system that could greatly benefit from it.

---

### Post by formaldehyde_spoon on 2010-09-11
I'm not in the US, so I don't think the cost of shipping would be worth it for you ;)

---

