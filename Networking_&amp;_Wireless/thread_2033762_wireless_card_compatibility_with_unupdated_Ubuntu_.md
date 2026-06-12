---
title: "wireless card compatibility with unupdated Ubuntu 9.10"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by haplorrhine on 2012-07-26
I want a usb wireless adaptor that will immediately work with Ubuntu 9.10 without requiring any updates from the internet.
From [this page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported/"), I can access pages about card type compatibility. Example:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#PCMCIA)
However, I don't understand the info on those pages. **Supports network install** is probably what I need, but I don't know if that will apply for older versions of Ubuntu. Maybe **Works "out of the box"** too?

---

### Post by bakegoodz on 2012-07-28
OK. Looked up your kernel on Distrowatch you have 2.6.31. I'm partial to Atheros chipset's Linux support. The following chipsets are supported by the well supported ath9k driver:
AR5008:

    AR5418+AR5133 (>= 2.6.27) AR5418 = DB 11n PCIe, AR5133 = 3x3 DB 11n

    AR5416+AR5133 (>= 2.6.27) AR5416 = DB 11n PCI

    AR5416+AR2133 (>= 2.6.27) AR2133 = 3x3 SB 11n 

AR9001:

    AR9160 (>= 2.6.27) DB 11n

AR9002:

    AR9220 (>= 2.6.27, an AR9280 card over PCI) 2x2 DB 11n PCI

    AR9280 (>= 2.6.27) 2x2 DB 11n PCIe

    AR9281 (>= 2.6.27) 2x2 SB 11n PCIe

    AR9285 (>= 2.6.29) 1x1 SB 11n PCIe

This what I recommend is go to [http://www.wikidevi.com/wiki/Special:BrowseData/Wireless_adapter?Brand=Atheros](http://www.wikidevi.com/wiki/Special:BrowseData/Wireless_adapter?Brand=Atheros)
Click on the type of adapter your looking for under "Interface:"
Then go through the adapters finding ones that have the chipsets listed in this post.

---

### Post by kurt18947 on 2012-07-28
I do know the wifi adapters I'm using will NOT work on 9.10.  The only adapter I've used that might work on a distro that old might be this Trendnet.  It was my wifi adapter for updating fresh installs when I first started messing with Linux because it just worked, no additional firmware, software or tweaking required.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152)

---

### Post by bakegoodz on 2012-07-29
Yes the 2.6.31 kernel has support for the Trendnet TEW-424UB It uses the RTL8187 module.

---

### Post by kurt18947 on 2012-07-29
> **bakegoodz said:**
> Yes the 2.6.31 kernel has support for the Trendnet TEW-424UB It uses the RTL8187 module.

I think it's an RTL8187B. Some plain 8187s had issues I believe.  I found the 8187B kinda slow even for a G speed device but it *was* and *is* reliably plug 'n' play.

---

### Post by haplorrhine on 2012-08-01
Thank you for the responses, but an alternate solution was implemented by the time I could view this thread again.  It was the work of someone else, but it looks like they just downloaded some packages and transferred them over to my laptop.

bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3
[http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)

fakeroot_1.14.4-1ubuntu1_**i386**
[http://packages.ubuntu.com/lucid/i386/fakeroot/download](http://packages.ubuntu.com/lucid/i386/fakeroot/download)

patch_2.6-2ubuntu1_**i386**
[http://packages.ubuntu.com/lucid/i386/patch/download](http://packages.ubuntu.com/lucid/i386/patch/download)

---

