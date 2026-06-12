---
title: "best usb wifi adapter for ubuntu on dell laptops"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by c2tarun on 2011-10-16
Hi friends.
I am using ubuntu 11.04 on my dell laptop. Dell usually provide broadcom wifi card with laptops. ubuntu dont support these cards well.
Earlier to this I was facing a lot of issues with previous ubuntu versions. Now I again started facing issues, ubuntu is detecting the wifi card but not able to search any network.

Now I decided to buy a new usb wifi adapter, can anyone suggest me which adapter should be best for me?
I am using Dell Inspiron N4010.
Is it possible to disable internal wifi card and use external usb wifi adapter in ubuntu?

Thanks

---

### Post by gareththered on 2011-10-16
Intel based ones seem to work well.  I've also used Belkin USB ones, but the problem with them is that you cannot guarantee what chipset they use.

In the past I've replaced the internal WiFi card in laptops to work around WiFi problems (cheap on eBay), but I know that the BIOS on some Dells will not allow this.

Hope this helps.

---

### Post by c2tarun on 2011-10-16
> **gareththered said:**
> Intel based ones seem to work well.  I've also used Belkin USB ones, but the problem with them is that you cannot guarantee what chipset they use.

In the past I've replaced the internal WiFi card in laptops to work around WiFi problems (cheap on eBay), but I know that the BIOS on some Dells will not allow this.

Hope this helps.

I cannot replace internal wifi card as it will violate the warranty. but I cannot complain to dell as well because then they will ask me to install windows. I decided to buy dlink one, is it possible to disable internal card and use only external?

---

### Post by cottfcfan on 2011-10-16
You can just blacklist the modules for your internal card.
run:
```
lsmod
```
and see whats being used.
The best usb adaptor ive used is an Edimax EW7318USg, works on everything, cheap as well.

---

### Post by c2tarun on 2011-10-16
Finally after getting frustrated with my broadcom wifi card, I purchased a belkin's usb wifi adapter, and now its working like a charm.
:) I didn't even have to configure or do anything, I just plugged and it automatically connected to the wifi availabe :popcorn:

---

### Post by c2tarun on 2011-10-16
Now I am facing a new problem. :( that wifi card is working fine on ubuntu but not working on kubuntu. Why so?
 
Modification: card is not working on KDE installed in ubuntu, but its working fine on KUBUNTU.
 
Can anyone please guide me to any tutorial to block internal wifi card.

---

