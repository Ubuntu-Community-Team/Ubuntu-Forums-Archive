---
title: "Wired and wireless internet"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by am6465 on 2010-07-02
Hey guys,

I was wondering if it's possible to connect to the Internet via ethernet and wifi at the same time. Aside from parallelism issues that might arise, is there a reason that a browser couldn't try to delegate part of the work onto the wireless network and part onto the wired network?

Thanks

---

### Post by zmjjmz on 2010-07-02
The only reason I could see a need for this is if you need some information sent out over an unsecured wifi network to throw off your pursuers, while sending some other information over ethernet securely, in which case you really shouldn't be posting this in a public forum.

That said, it is possible to connect to both as ethernet and wifi are handled by different interfaces (in my case, eth0 and wlan0), but I'm not sure how you would tell a browser to use a specific interface.

---

### Post by Iowan on 2010-07-02
My laptop used to connect to my home network (via cable) and my neighbor's wireless. I was never really sure which connection it was using for what. :)

---

### Post by tubezninja on 2010-07-02
There's a prcoedure for bonding two ethernet cards, and the tools exist in ubuntu.  No idea how it would work with wireless.  My guess is given the added latency of the wireless card, it might make your performance WORSE than if you just used eth0.

But if you want to give it a go, here it is:

[http://www.mygeekproject.com/?p=611](http://www.mygeekproject.com/?p=611)

---

### Post by am6465 on 2010-07-03
The only reason I asked was out of curiosity. I was looking at it from a possible performance boost but I know next to nothing about how they work. Thanks for all the replies

---

