---
title: "router advice"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by boregard on 2012-12-12
Hi, i am wanting to purchase a Cisco-Linksys WRT54GL router because i heard it was linux based.I was wanting to know if you can use it with cable internet? has anyone had any experience with one? any advice will be appreciated, thanks

---

### Post by haqking on 2012-12-12
> **boregard said:**
> Hi, i am wanting to purchase a Cisco-Linksys WRT54GL router because i heard it was linux based.I was wanting to know if you can use it with cable internet? has anyone had any experience with one? any advice will be appreciated, thanks

99.9% of all home/residential routers run Linux or some type thereof. (I am making that figure up by the way)

According to its manual yes it accepts cable, though I dont know if it supports high speed such as vDSL

It only offers 54G Wireless though, which will slow down a Fast Internet Connection considerably, for example i have a 75Mbps connection and if i used wireless it would be slower than my Internet itself

---

### Post by chili555 on 2012-12-12
I have a Linksys WRT54G and have used it perfectly well with both cable and DSL. I am quite confident the GL will also work perfectly once configured.

---

### Post by ahallubuntu on 2012-12-12
You don't need to get the WRT54GL specifically.  The WRT54G itself comes in many versions.  I have a version 4, which as I  understand it is basically the same hardware as the WRT54GL.  You might be able to find some V4's cheaply.

You can run the Linux-based DD-WRT firmware on almost any WRT54G router, no matter what version, but versions 5 and newer can't run the full image (with OpenVPN, etc.)  WRT54GL can run the full image.  Check the router database on [www.dd-wrt.com](www.dd-wrt.com) to confirm which versions of the router run what version of the firmware.  There are other Linux-based firmwares like Tomato and OpenWRT as well.

The WRT54G/GL is a great router to use as a gateway - rock-solid.  But I probably wouldn't buy one unless you can get one for very cheap.  I'd probably buy a newer router instead that supports 802.11n - like the Asus RT-N13U/B1 which is sometimes on sale.  I have a couple of those, too.  They run a full image of DD-WRT too.

---

### Post by haqking on 2012-12-12
> **ahallubuntu said:**
> You don't need to get the WRT54GL specifically.  The WRT54G itself comes in many versions.  I have a version 4, which as I  understand it is basically the same hardware as the WRT54GL.  You might be able to find some V4's cheaply.

You can run the Linux-based DD-WRT firmware on almost any WRT54G router, no matter what version, but versions 5 and newer can't run the full image (with OpenVPN, etc.)  WRT54GL can run the full image.  Check the router database on [www.dd-wrt.com]("http://www.dd-wrt.com") to confirm which versions of the router run what version of the firmware.  There are other Linux-based firmwares like Tomato and OpenWRT as well.

The WRT54G/GL is a great router to use as a gateway - rock-solid.  But I probably wouldn't buy one unless you can get one for very cheap.  I'd probably buy a newer router instead that supports 802.11n - like the Asus RT-N13U/B1 which is sometimes on sale.  I have a couple of those, too.  They run a full image of DD-WRT too.

I am assuming the OP doesnt know too much about routers to be asking the question, I dont think buying one then potentially bricking it with a new firmware is good idea ;-)  The OP didnt mention DD-WRT, they just said Linux based, which most router IOS is certainly the Linksys/Cisco ones

---

### Post by boregard on 2012-12-12
yes you are correct, i don&#8217;t know anything about routers. i am currently paying rent on one from time/warner cable and looking for a good replacment. Thanks to all for your input.

---

### Post by haqking on 2012-12-12
> **boregard said:**
> yes you are correct, i don&#8217;t know anything about routers. i am currently paying rent on one from time/warner cable and looking for a good replacment. Thanks to all for your input.


Well check with your ISP if you can switch routers, and also any issues they will no longer support if not using their router I suspect.

And as I mentioned above if you have a fast Internet then 54g might not be enough for wireless if you are to use wireless, and if you get one that has Wireless N then to get the speed throughput you need AES encryption or it will drop to 54Mbps  anyways.

Peace

---

### Post by ahallubuntu on 2012-12-12
Installing DD-WRT on a Linksys WRT54G is very easy.  The chances of bricking one are small.  In any event, this is old router that can be bought cheaply used.  I paid $15 USD for each of mine a few years ago.  Nowadays you might find them even cheaper.  So what if you brick a cheap used router?  You lost $15 or less?  But you might learn something.

---

### Post by haqking on 2012-12-12
> **ahallubuntu said:**
> Installing DD-WRT on a Linksys WRT54G is very easy.  The chances of bricking one are small.  In any event, this is old router that can be bought cheaply used.  I paid $15 USD for each of mine a few years ago.  Nowadays you might find them even cheaper.  So what if you brick a cheap used router?  You lost $15 or less?  But you might learn something.


yes it is, but the OP is inexperienced and doesn't know much about routers, they just want to buy one that works with cable.

If they want to do some learning and don't mind the possibility of bricking it then of course DD-WRT or similar is a good idea, but I think they just want to know if they can buy this router and if it will work with Cable, in which case the answer is yes.

Cheers

---

### Post by CharlesA on 2012-12-12
> **haqking said:**
> Well check with your ISP if you can switch routers, and also any issues they will no longer support if not using their router I suspect.

And as I mentioned above if you have a fast Internet then 54g might not be enough for wireless if you are to use wireless, and if you get one that has Wireless N then to get the speed throughput you need AES encryption or it will drop to 54Mbps  anyways.

Peace

Pretty much. The one the OP is paying for is probably a modem/router combo (which most ISPs seem to be using nowadays), so they would need a modem in addition to the router.

> **ahallubuntu said:**
> Installing DD-WRT on a Linksys WRT54G is very easy.  The chances of bricking one are small.  In any event, this is old router that can be bought cheaply used.  I paid $15 USD for each of mine a few years ago.  Nowadays you might find them even cheaper.  So what if you brick a cheap used router?  You lost $15 or less?  But you might learn something.

I haven't bricked a router (yet), but for someone who doesn't know what they are doing and runs into problems - such as having to hex edit the firmware to get it to flash on a dlink, it can be tricky, but not really difficult.

It depends on what the user wants to do and if they are fine with the stock firmware, they should stick with the stock firmware.

---

### Post by haqking on 2012-12-12
> **CharlesA said:**
> Pretty much. The one the OP is paying for is probably a modem/router combo (which most ISPs seem to be using nowadays), so they would need a modem in addition to the router.

.

yes good point, to the OP you will probably need to buy a cable modem also, unless you choose a cable modem/router combination, your router of choice is just a router and does not have a cable modem in it.

Peace

---

### Post by boregard on 2012-12-13
Thanks guys for all the advice. I&#8217;ll mark this thread solved. best regards

---

