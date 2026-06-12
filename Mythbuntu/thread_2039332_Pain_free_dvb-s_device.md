---
title: "Pain free dvb-s device?"
date: 2012-08-08
forum: Mythbuntu
---

### Post by aovermy on 2012-08-08
It can be either USB or PCI, but not PCIe. I'm just looking for a simple DVB-S2 device that will work out of the box with mythbuntu 11.10 (although if it's a simple matter of get the drivers and compile them or get the firmware or a simple patch, I can do that). The device must be able to drive a USALS motor and handle symbolrates from the absurdly low (3500-ish) to the absurdly high (30000) and everything in between. 

I have a dw2104d that will not find its frontend, a technotrend 1600 that doesn't appear to be able to tune anything at all, and a prof7301 that works perfectly (with a patch) but alas they've changed the model such that new cards won't work. The prof7301 does everything well in mythtv, but I'm looking to set up a second dish and need a second receiver card.

---

### Post by nickrout on 2012-08-08
> **aovermy said:**
> It can be either USB or PCI, but not PCIe. I'm just looking for a simple DVB-S2 device that will work out of the box with mythbuntu 11.10 (although if it's a simple matter of get the drivers and compile them or get the firmware or a simple patch, I can do that). The device must be able to drive a USALS motor and handle symbolrates from the absurdly low (3500-ish) to the absurdly high (30000) and everything in between. 

I have a dw2104d that will not find its frontend, a technotrend 1600 that doesn't appear to be able to tune anything at all, and a prof7301 that works perfectly (with a patch) but alas they've changed the model such that new cards won't work. The prof7301 does everything well in mythtv, but I'm looking to set up a second dish and need a second receiver card.

Can't directly answer your question but if you know the prof7301 does the job, perhaps ebay, or your local equivalnet, can supply one?

---

### Post by aovermy on 2012-08-29
Thanks. Unfortunately, the prof tuner providers didn't change the model number when they changed the hw so I can't know if I'm getting an old prof7301 that is supported by linux or a new prof7301 that isn't. 

However, I solved the problem with the usb brother of the prof7301, a prof7500. Seems to be pretty close in quality to the pci. A real virtue of the stv0900 driver is its support of blind scanning, something useful for North American & South American dvb-s users, but probably not to folks in Europe or New Zealand.

Now if I put in a new pole (the one the new dish is on is crooked!) I'll really be in business. But at least even with a crooked pole, I get quite a few of the channels I like and it works well for scheduling conflict avoidance.

---

### Post by nickrout on 2012-08-29
> **aovermy said:**
> Thanks. Unfortunately, the prof tuner providers didn't change the model number when they changed the hw so I can't know if I'm getting an old prof7301 that is supported by linux or a new prof7301 that isn't. 

However, I solved the problem with the usb brother of the prof7301, a prof7500. Seems to be pretty close in quality to the pci. A real virtue of the stv0900 driver is its support of blind scanning, something useful for North American & South American dvb-s users, but probably not to folks in Europe or New Zealand.

Now if I put in a new pole (the one the new dish is on is crooked!) I'll really be in business. But at least even with a crooked pole, I get quite a few of the channels I like and it works well for scheduling conflict avoidance.

Good to know. Supported DVB-S2 cards are nowhere near as easy to find as straight DVB-S. 

I hope you'll contribute to the community and add a page about your experiences on the linuxtv wiki.

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

Mythtv wiki deprecates specific hardware pages, because the support info should be on linuxtv.org. It may pay to add a page on the mythtv wiki pointing to your linuxtv wiki page though. 

BTW how does a USB device supply the LNB voltage? Does it have an external power supply?

---

### Post by aovermy on 2012-08-29
Yes, external power supply. My motor requires 18V so getting that off the usb bus is a non-starter.

I'll check out that wiki page. I mainly got my info from the mythtv wiki (which has a link to an important dvb patch) and a couple FTA forums.

Amy

---

### Post by updatelee on 2012-11-04
So what chipsets do the new 7301's have ? I didnt know they changed them. hopefully its minor so we can get it up and running in linux. The Prof line so far has been pretty good thus far.

---

### Post by AlecJ on 2012-11-05
[HTML]http://www.tbsdtv.com/products/tbs8922-dvb-s2-tv-tuner-pci-card.html[/HTML]

I use this with 12.04, you need to install the drivers but that's no bother.

It says motor support? Not sure I use a fixed dish with multi LNB's

---

