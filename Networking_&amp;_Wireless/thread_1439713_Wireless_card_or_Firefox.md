---
title: "Wireless card or Firefox?"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by jesseejames on 2010-03-26
I just did a new install of ubuntu Karmic on a Gateway Solo 5350 laptop with a Belkin Wireless G notebook card. I booted up next to my local hotspot and was able to detect the wireless networks and connect to the free one. At least for a few minutes. I was unable to access this forum with Firefox or anything else with firefox before I received a disconnect notice and then a reconnect notice. I gave up and looked at the error console in Firefox and found this error. I am totally new to ubuntu so I need lots of help in working out this problem so I can get online at the hotspot instead of trying to solve problems with my slow dialup windows 98 connection. 



uncaught exception: [Exception Component returned failure code:Ox80040111 (NS ERROR_NOT_AVAILABLE) [nls XMLHttp Request.status]"NS result:"Ox80040111(NS_ERROR_NOT_AVAILABLE)"locatio n: "JS frame:: Chrome://ubufox/content/start page.html:: anonymous :: line 51" data: no]

I am totally lost as to what to do in order to get online. I am greatly impressed with the other aspects of ubuntu. Please help?

---

### Post by jesseejames on 2010-03-26
is it my card or is it firefox?

---

### Post by nothingspecial on 2010-03-26
On the off chance you`ve set up your forum thingymabob to email you if you get a reply - 

go accessories > terminal and copy and paste

```
sudo lshw -C network
```

Then copy and paste the output here or in your Ubuntu is completely rubbish thread - either will do.

---

### Post by jesseejames on 2010-03-26
cannot copy and paste but here is the output unless i make a typing error
 
*network
description: Ethernet interface
product:82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
vendor Intel Corporation
physical id: 8
bus info: [EMAIL="pci@0000:02:08.0"]pci@0000:02:08.0[/EMAIL]
logical name: eth0
version: 41
serial: 00:00:f0:6a:5b:f1
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt=f
d 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion
=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlayency=56 mingnt
=8 multicast=yes port=MII speed=10MB/s
resources: irq:10 memory:e0200000-e0200fff iport:9400(size=64)
*-network
description:Wireless interface
product: Belkin
vendor: Belkin
physical id:  1
bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
logical name: wmaster0
version; 20
serial: 00:17:3f:3l:e4:de
width: 32 bits
clock: 33MHz
capabilities: pm bus master cap list logical ethernet physical wireless
configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 ming
nt=32 multicast=yes wireless=IEEE 802.11bg
resources: irq10 ioport:9800(size=256) memory:2c000000-2c0003ff

---

### Post by Capital E on 2010-03-26
try an Ethernet connection to get new browser and test if it is firefox.

If it's your card, maybe it's the driver. CD drivers suck, so make sure to **right click to execute** .exe drivers in wine:


Find your driver here:
[http://en-us-support.belkin.com/app/answers/detail/a_id/302](http://en-us-support.belkin.com/app/answers/detail/a_id/302)

---

### Post by nothingspecial on 2010-03-26
I promise you I will look into it later.

Kids go to bed in 1 hour 9.30 uk time. After that ( and a beer) I`m at it.

---

### Post by jesseejames on 2010-03-26
I will try a new install of firefox when I can access the internet with something greater than my dialup.  Thanks for the info I will get back and let you know hoe I made out.  My frustration is partly due to not having high speed internet available except at hotspots.

---

### Post by nothingspecial on 2010-03-26
Ouch !

You`ve got a bad one there. As in (as far as I can tell from google) this card does not like linux.

I`ve seen a few people manage it but it doesn`t look good.

Decision time -

1. Prepare for a whole lot of messing about and terminal stuff that may or may not get your card working.

2. Buy a new one that does work.

3. Use windows instead.

I`m prepared to help you achieve whichever course you choose.

This is why you got no help btw. This looks like a tough one.

Someone once told me, as a rule of thumb, about 70% of normal hardware (printers, wireless, cameras etc) work straight away with linux. 15% you can make work with alot of messing about. The other 15% will not work - ever - no matter what you do - unless you reverse engineer and code the driver yourself.

Your wireless card is one of the last 2.

---

### Post by jesseejames on 2010-03-26
Thanks so much for your help I was going mad.  I am going to buy a new card as this one did not work very well in windows either. 
 Do you have any suggestions as to one that will work well in linux right out of the box? 
 I can just reinstall Unbuntu after I get it and go from there.  I only have dialup available at home so I need to be able to use the internet from a hotspot for everything except e-mails.

---

### Post by nothingspecial on 2010-03-26
Look into it. I don`t have a definitive list. My netgear one has always worked. 

Take your laptop/netbook to the shop/store and ask if you can test it.

That`s what I do.

I find that independent computer shops are far more willing to help than national chains.

Google compatability, although be aware. Some (very few) cards that used to work no longer do........although that is usually fixable.

---

### Post by jesseejames on 2010-03-26
Thats a great idea I never thought of doing that. Thanks again.  I will get back here when I have a new card that works.

---

