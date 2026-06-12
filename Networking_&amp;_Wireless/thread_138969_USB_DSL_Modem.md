---
title: "USB DSL Modem"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by zzz@tkz on 2006-03-02
I understand that there are some problems with USB modems, and I was wondering where I could get the list of modems that can be used.


I have a Netopia DSL modem.

---

### Post by SectionThree on 2006-03-02
My experience with DSL devices is that they all work with Ubuntu, regardless of whether there's official support or not. Just plug in your modem and see if it works right away or not. If it doesn't, do a search on Synaptic for the appropriate driver software (or alternately, go to the manufacturer's website and see what they have to say).

A while ago I had a problem getting my external USB CD burner to work with Ubuntu (the Debian site claims there is NO support for USB CD burners), but I experimented with various software programs until I found one that worked really well (Graveman).

The point here is that no matter what kind of hardware you're trying to get working with Ubuntu, there's probably something out there in open-source land that will do the trick. Just keep trying and be patient...

---

### Post by zzz@tkz on 2006-03-02
Ah. Never thought to check the manufactuar's site. Thanks.

---

### Post by zzz@tkz on 2006-03-03
(Sorry 'bout the double post)

I checked netopia's site, and server other websites, and can't find the driver for it.

It seems that it is a Cayman 3300 Series USB Netopia DSL Modem.

---

### Post by mips on 2006-03-04
Hmm, still dont know exactly which one you have ???

[http://www.netopia.com/equipment/products/3000/3300_res_models.html](http://www.netopia.com/equipment/products/3000/3300_res_models.html)

Every model except the 3342/52 Pocket has Ethernet ports so just use the Ethernet port and save yourself a lot of trouble.

If you have the misfortune to have the 3342 or 3352 Pocket modem then you need to look at this driver, [http://accessrunner.sourceforge.net/index.shtml](http://accessrunner.sourceforge.net/index.shtml)

---

### Post by zzz@tkz on 2006-03-04
Yea, it seems that I do have the Pcket modem.


Can I put that driver on my flash drive, then extract it within linux?
(Its format is FAT32)

And how do I install it :P?

---

### Post by mips on 2006-03-05
Should be able to put it on a flash drive but do you need any other dependencies etc ?

Search these forums for "access runner" as I'm sure others have been there before.

---

