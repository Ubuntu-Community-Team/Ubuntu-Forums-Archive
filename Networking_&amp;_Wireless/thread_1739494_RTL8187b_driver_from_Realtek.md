---
title: "RTL8187b driver from Realtek"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by sctechlaw on 2011-04-26
Mama told me "it never hurts to just ask" and she was right, as usual. :D  Frustrated with trying to get my little Encore  USB wireless adapter to work on several flavors of Linux (Ubuntu 10,10, ElementOS, Xubuntu, and Puppy), I emailed tech support at Realtek. I asked where is the Linux driver for [this product]("http://www.newegg.com/Product/Product.aspx?Item=33-180-017")? I did this because there were no Linux drivers posted on their site and everyone here (and on Newegg) is jumping though hoops trying to get a working wireless connection with the Encore and similar dongles that use the RT8187b chipset. I didn't expect an answer, but felt better after my little vent. 

Lo and behold, a few hours later I get an email from Realtek (thanks Jerry!) with a driver. I am *duly* impressed. Realtek needs to promote Jerry -- a beacon of customer service in the age of the "get lost" school of customer relations. I have attached the driver below.

Caveat: I have not yet compiled the driver, so I don't know much more about it than I've said already, although the archive appears to contain the source code. I was just so nonplussed that I thought I'd post it right away so that those more experienced than I could have a look see.

Manna from heaven ...

---

### Post by walt.smith1960 on 2011-04-26
RTL8187b doesn't just work out of box?

---

### Post by sctechlaw on 2011-04-26
> **walt.smith1960 said:**
> RTL8187b doesn't just work out of box?
It worked out of the box only on Ubuntu, but quickly slowed to a crawl and continues to have massive performance issues, and also drops connections frequently (constantly). There are many posts about this problem on this board and others. I was unable to find a nix driver for it, which is what prompted me to mail them after a day spent watching a high-end quad core beast behave like it was using dial-up in 1989. It will be a few days before I have time to test it as I wasted so much time on the issues that other things fell behind and I have to attend to them first. Hopefully someone can look at what Realtek provided and make progress. I sure hope I can too when I have a chance to look at it further.

---

### Post by walt.smith1960 on 2011-04-26
Thanks.  I've recommended the TrendNet TEW-424UB adapter in the past because mine has been fine, no performance issues and has been reliable. I'm using N speed adapters now but I still use the old TrendNet to get an initial wifi connection to update new installs and install any proprietary software for video or wifi that don't work properly out of the box.  I do that because the connection has been plug & play for me.  Perhaps the recent kernels have become problematic for that chipset or perhaps not all RTL8187b based devices behave alike.   Sorry to hear you're having problems and hope you get it sorted out.

---

