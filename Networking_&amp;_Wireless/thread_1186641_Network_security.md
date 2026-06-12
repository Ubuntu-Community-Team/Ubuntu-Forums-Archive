---
title: "Network security"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2009-06-13
I've got a Belkin PCMCIA wireless network card on my laptop with BCM4306 chip. It is supported by the kernel b43legacy driver but the connection is painfully slow (1Mb/s). If I use ndiswrapper, the connection is 54 MB/s, but the problem is ndiswrapper does not support WPA security. After trying all tricks and failing to make it work with WPA I decided to hide the access point and use MAC filtering dropping the WPA security altogether. I know that it is less safe than WPA but how bad is it?

---

### Post by jimv on 2009-06-13
I've been dealing with a similar problem on my laptop.  Connection sucked with the native driver, and WPA didn't work with ndiswrapper.  I ended up doing the easy fix and checking a driver list to see which models where best supported, and then bought one off eBay for cheap.

Here's the list if you want to look:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by foxy123 on 2009-06-13
> **jimv said:**
> I've been dealing with a similar problem on my laptop.  Connection sucked with the native driver, and WPA didn't work with ndiswrapper.  I ended up doing the easy fix and checking a driver list to see which models where best supported, and then bought one off eBay for cheap.

Here's the list if you want to look:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
Thanks a lot. It is a bit tricky. I have looked at eBay and found Netgear WD511T which looks supported. Though its interface is Cardbus not PCMCIA and theer are a few topics on the forum of people complaining that it stopped working or does not work at all. How did you choose yours?

---

### Post by jimv on 2009-06-14
This one looks like it would work:

[http://desc.shop.ebay.com/items/?_nkw=wg511t&_sacat=45000&LH_TitleDesc=1&_trksid=p3286.m270.l1313&_sop=1&_odkw=2511CD2&_osacat=45000](http://desc.shop.ebay.com/items/?_nkw=wg511t&_sacat=45000&LH_TitleDesc=1&_trksid=p3286.m270.l1313&_sop=1&_odkw=2511CD2&_osacat=45000)

---

### Post by foxy123 on 2009-06-14
> **jimv said:**
> This one looks like it would work:

[http://desc.shop.ebay.com/items/?_nkw=wg511t&_sacat=45000&LH_TitleDesc=1&_trksid=p3286.m270.l1313&_sop=1&_odkw=2511CD2&_osacat=45000](http://desc.shop.ebay.com/items/?_nkw=wg511t&_sacat=45000&LH_TitleDesc=1&_trksid=p3286.m270.l1313&_sop=1&_odkw=2511CD2&_osacat=45000)

Thanks a lot. I have ordered a different one as I am in the UK. MSI CB54G2, which is advertised to work with Linux (Ubuntu) and has WPA security. We'll see how it will work when arrives.

---

