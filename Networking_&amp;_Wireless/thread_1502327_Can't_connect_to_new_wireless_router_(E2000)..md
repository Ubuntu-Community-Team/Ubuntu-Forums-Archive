---
title: "Can't connect to new wireless router (E2000)."
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-06-05
I just bought a Linksys E2000 wireless router yesterday. Anyone know how I can start to solve this problem - My wireless card, Asus PCE N13 doesn't pick up a signal/connect at all yet. I would love to know where to start to diagnose this issue. 

thanks,
Randy

---

### Post by pepsifx357 on 2010-06-19
Haha Same here.  I tried using Windows with the CD and it didn't work either.  It wanted me to call customer service and I don't EVER do that.  I let you know if I get it running.  Right now, I'm trying WINE with the cd.

---

### Post by Goo12 on 2010-08-24
I am having the same problem on my Asus Eee PC 1000.  Any resolutions yet?

I recently installed Ubuntu 10.04 from 9.10.  It worked fine with 9.10 but keeps dropping in 10.04.  My winXP machine and my bothers Win7 machine connects with out hesitation.  Also my Ubuntu machine does not have a problem connecting to any other access point.  

I'm going to try to find my CD and re-setup my router maybe there is a setting messing with it.

---

### Post by Michelle de Vries on 2010-12-02
We bought this router today for our home network.  We use various versions of ubuntu: 9.10, 10.04, and 10.10.

Cisco is amazingly unhelpful in not providing a user manual in booklet form or even in electronic form on the CD that comes with the router.  After downloading the manual from their website, I found that you can access the manual "web-based" router controls by using address 192.168.1.1  (note this is different from other routers I've used which have all used 192.168.0.1)  

I should back up and say that it seems important which order you turn your modem, router, and computer on.  Turn the modem on, then the wired computer which you'll control the router with, then finally the router.  Once in, the router defaults should get your wired computer on the 'net.  Log in to the web-based controls by typing into your browser the address 192.168.1.1  .  Use userID: admin and password: admin.  You can change these once in under the management section.

In the wireless section, I had to use the 2.4GHz and not the 5GHz.  My wireless computers wouldn't even "see" the 5Ghz.  I suspect this is what has caused some problems for some folks.  You can setup some of your security stuff in here too.

I realize this is sort of a "hand-waving" sort of suggestion, but I suspect you just need a couple of hints to get going. Hope it works.

---

