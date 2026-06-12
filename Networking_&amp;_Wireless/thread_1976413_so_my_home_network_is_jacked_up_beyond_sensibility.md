---
title: "so my home network is jacked up beyond sensibility. help?"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by sirspazzolot on 2012-05-08
[http://i.imgur.com/RECiA.jpg](http://i.imgur.com/RECiA.jpg)
 
that's the scenario. the middle option has been tried and confirmed on two different routers. we've also daisy chained them which, as expected, failed.
 
any ideas? we'll try restoring the routers to factory settings tonight but that wouldn't remedy the bottom case. Thanks in advance!

---

### Post by steeldriver on 2012-05-08
well I'm not familiar with your situation, but in my part of the world cable modems are often tied to the particular MAC address of the original attached device - you may be able to force the modem to register the new MAC, e.g.

[http://www.dslreports.com/faq/9089](http://www.dslreports.com/faq/9089)

or, if your router supports MAC cloning you can have it clone the MAC of your desktop

otherwise it's up to the ISP to reset it for you

---

### Post by sirspazzolot on 2012-05-09
we had two routers daisy chained off the modem for months and it worked fine, but suddenly stopped working. now when we have them daisy chained, the second router works but the first router only works for some devices (my laptop and ipod, but not my mom's laptop and ipad or our other laptop)

mummy dearest loves her router about as much as she loves me so that wasn't acceptable and we switched around our setup to try the scenarios in the picture. eventually it started working with just one router fairly consistently but if we plug in the second router it goes to the situation described above. is the first router getting overloaded somehow? it is pretty old. I'll play around this weekend with mac cloning but I have AP tests to study for so I should probably not risk breaking the internet until then haha

thanks for the tip!

---

### Post by steeldriver on 2012-05-09
The only reason I can think to daisy chain 2 routers is if you want to use the 2nd one as a dumb access point or switch not an actual router / gateway 

In that case you would need to make sure (a) to connect from a LAN port on the primary router to a LAN port on the 2nd "router" (i.e. *not* the WAN port that you would usually use) and (b) turn OFF any DHCP server on the 2nd "router".

I used exactly that configuration until recently with an old WRT54GL to provide wireless access on top of a wired-only Speedtouch DSL modem.

---

