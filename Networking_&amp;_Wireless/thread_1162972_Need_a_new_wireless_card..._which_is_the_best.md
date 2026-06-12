---
title: "Need a new wireless card... which is the best?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by The Switch Blade on 2009-05-18
I'm running ubuntu 9.04. I have a Belkin 4306 rev 03. I'm using ndiswrapper with some dell drivers (iirc) and have a pretty poor connection. My ISP came today to test the connectivity. I downloaded ~2mbps, and he got 8mbps. He told me that it's my card and that I need a new one.

So... what should I get? I also assume I'll have to reverse what I did with ndiswrapper, and unblacklist ssb/bcm34xx/legacy/b43, right?

---

### Post by The Switch Blade on 2009-05-18
bump

---

### Post by pawnrocket on 2009-05-18
It depends on what you do with it. If you have any interest in wireless password cracking you should get one from the list at the aircrack-ng website, those have monitor mode enabled. 

Other then that search for cards officially supported by ubuntu (if there is such a thing)

---

### Post by The Switch Blade on 2009-05-18
I don't need password cracking. We have a wireless router and I just need a good, solid connection to it.

---

### Post by pawnrocket on 2009-05-18
What kind of router?

---

### Post by The Switch Blade on 2009-05-18
> **pawnrocket said:**
> What kind of router?
Thomson RCA DCW725 Gateway 802.11b/g WEP 54Mb/s

---

### Post by pawnrocket on 2009-05-18
THOMSON TG123g

I generally keep to the company. Some People say using the same router and wireless can increase speed. I don't know if its true, but I don't see how it can hurt.

It apears to be supported.

---

### Post by ssam on 2009-05-18
beware that the wireless card manufacturers dont make the chipsets. so the name you see on the box (belkin, linksys etc) is different from the chipset (ralink, atheros, broadcom etc). even a particular model of wireless card may exist with different chipsets.

this is less of a problem these days as most chipsets are well supported on linux. however if you want to be sure that it will work buy from a linux friendly retailer. eg [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by WheelDweller on 2009-05-18
> **ssam said:**
> beware that the wireless card manufacturers dont make the chipsets. so the name you see on the box (belkin, linksys etc) is different from the chipset (ralink, atheros, broadcom etc). even a particular model of wireless card may exist with different chipsets.

this is less of a problem these days as most chipsets are well supported on linux. however if you want to be sure that it will work buy from a linux friendly retailer. eg [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Yeah, same for webcams, etc.

I *can* tell you what has worked for me:

An Atheros-based wireless card from Walmart (Yeah, really!) and _not_ a Belkin AP: the Belkin tends to overheat and hang when torrenting.

I was surprised to learn a friend had bought about 30 simple, D-Link Di-264 AP's and was now stuck with them.  I was even MORE surprised when I got one from him and started getting the full use from my wireless link!

Here is a special case: my trailer has the 'big' computer in it, with all the media and such, and it's connected by a 6-foot extension cable and simple antenna. It works really, really well. I have a simple Celeron 400mHz machine in there as a router/firewall/climate control. 

But the best I got was the Atheros chipset and the D-Link Di-264, even in rain, ice and snow. (We had all three)

---

