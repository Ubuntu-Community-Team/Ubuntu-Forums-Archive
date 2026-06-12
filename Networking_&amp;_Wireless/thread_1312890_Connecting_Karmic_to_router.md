---
title: "Connecting Karmic to router"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by damnated on 2009-11-03
I have two PCs at home, and i want to share the internet connection with a router. Home networking is not an option for multiple reasons.

I'm very new to this, so i'm not entirely sure what i should be doing. I plugged in my ethernet cable in to my router, and in to my pc. Ubuntu says wired network connected, but there is still no internet. 

Any ideas?

Also: i connect to the internet through a cable modem. The modem is also connected to the router, the router detects both the pc and the modem.

---

### Post by Iowan on 2009-11-03
> **damnated said:**
> I'm very new to this, so i'm not entirely sure what i should be doing.This is a good place to find out...
I don't yet have Karmic, so my advice may not be current. Easiest way to get some information is via terminal (Applications>Accessories>Terminal). Check (and post, if possible) **ifconfig -a** and **route -n**. This should show the IP address of your machine, and the IP address of the gateway it should be using. **less /etc/resolv.conf** should show which DNS servers you are using.

---

