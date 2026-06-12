---
title: "Help buying new wireless router"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2009-03-21
I'm looking to buy a new wireless router because mine is really old and only supports WEP. I wanted to know what would be the best router for security and also has decent speeds. I've been searching around for a while and I am really at a loss here.

---

### Post by lindsay7 on 2009-03-21
I would think that the first thing you would want to do is determine what type of wireless adaptors you have. i.e. are the b,g, or n compatable devices. They you can get some advice on what router might be best for you.  Router speed will not help if you wireless devices are not matched to it,

---

### Post by brandon88tube on 2009-03-21
Well I did forget to mention what type I wanted, but my laptop is a/b/g compatible and my other device needs to be replaced anyways if I get a new router. I was possibly looking at getting one with n capabilities just in case I get a new device that also works with n, so that I could use those speeds. Like I said thats not really important to me so much as security is. Security is priority otherwise there would be no point in me getting a new router.

---

### Post by mooksh83 on 2009-03-21
If you need a broadband router then go for ZyXEL P320W, else, for ADSL 2+ go for ZyXEL P-660HW. ZyXEL is well known for stability and security as well.

---

### Post by Therion on 2009-03-21
Behold:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190)

You need look no further.  Jeez that's a hell of a deal, too...  $65 and free shipping.

If you really want Wireless-n I'd say look at this, roughly the same price but I have no personal experience with it:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156052](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156052)

---

### Post by brandon88tube on 2009-03-21
I was wondering if any wireless n routers worked with Tomato firmware. I've been looking to try this firmware out.

---

### Post by bigbencg on 2009-03-21
You may be getting ahead of yourself.  There is no perfect security solution, layers of security are the key.  Having an encrypted wireless network is great, WPA is great.  If you can layer MAC filtering on top of WPA, that is even better.  Not only is your data encrypted in transmission, you have to be using a specified adapter to even talk to the network.  The choice of standards is yours, ask yourself what you are actually transferring over your wireless network and do you really need N speeds.  The link Therion posted is a good deal, and more than likely offers the security setup I described.  Many routers offer MAC filtering and an array of encryption schemes.  How much do want to spend, do you really need the speeds, why buy new wireless adapters if you don't have to.

As for the firmware, my thoughts are if it works with the firmware it comes with why change it?

---

### Post by lindsay7 on 2009-03-22
+1 on that! If you can get the router to work out of the box with your systems. I would not mess with the firmware.

---

### Post by brandon88tube on 2009-04-01
Just in case anyone was wondering, I went with the d-link dir-655 xtreme n gigabit wireless router. I have to say that it was a really good choice.

---

### Post by freonchill on 2009-04-01
bigbencg - mac filtering is pointless b/c mac addresses can be spoofed

brandon88tube - so much for your desire to get a router with tomato/dd-wrt support

---

### Post by bigbencg on 2009-04-05
> Just in case anyone was wondering, I went with the d-link dir-655 xtreme n gigabit wireless router. I have to say that it was a really good choice.

I was wondering, I hate it when a thread dies without confirmation or success or failure from the thread creator.

freonchill......

> bigbencg - mac filtering is pointless b/c mac addresses can be spoofed

Just because the possibility exists that someone could obtain a MAC address and spoof it doesn't mean it's pointless.  It is a layer of security that will slow down an attacker.  I never said to only use MAC filtering, I made mention of it because it would make is wireless network security stronger if combined with one or more methods or security.

Does that mean since a WEP key can be broken or even obtained through any number of ways that encryption is pointless as well?

---

### Post by brandon88tube on 2009-04-05
> **bigbencg said:**
> I was wondering, I hate it when a thread dies without confirmation or success or failure from the thread creator.

Yeah, I know what you mean. I really was only looking at the tomato firmware because it had a better looking interface with more options then I was used to, but with this new one I have I am perfectly fine with how it is.

---

