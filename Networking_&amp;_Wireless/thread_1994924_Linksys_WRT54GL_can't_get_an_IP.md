---
title: "Linksys WRT54GL can't get an IP"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Swanynovin on 2012-06-03
I have bought a Linksys WRT54GL router. When all is connected and ready it must work, but it doesn’t. I have reset  a couple of times, I have researched in the Internet for two days, I have even play with the settings! But nothing worked, so it's time to ask for help :(. The problem is that the the router can't get an IP from my ISP, I think. Do you have any idea?

Some data:

[LIST]
[*]Router: Linksys WRT54GL (1.1)
[*]Firmware: original and DD-WRT (v4 mini generic), I have tried both and I got the same error.
[*]OS: Ubuntu 12.04 x64 and Windows 7 Ultimate x64 (none of them works)
[/LIST]
If you need any other information, just ask :P!

---

### Post by steeldriver on 2012-06-03
what is on the OTHER side of the WRT54? DSL modem? Cable modem?

does the computer connect to the WRT54 OK? can you navigate to the WRT54 setup screen?

---

### Post by Swanynovin on 2012-06-04
> **steeldriver said:**
> what is on the OTHER side of the WRT54? DSL modem? Cable modem?
Sorry, I don't know how to answer that. It is like this:
[CENTER][IMG]http://www.technologicalzombie.net/wp-content/uploads/2011/12/linksys_wrt54g_back.jpg[/IMG]
[/CENTER]
The power is connected to the electricity. LAN port is connected to the computer, and WAN port is connected to a plug in the wall (sorry, but I don't know how to call this on English). I think that all connections are fine.

> **steeldriver said:**
> does the computer connect to the WRT54 OK? can you navigate to the WRT54 setup screen?
Yes, I can :P.

---

### Post by steeldriver on 2012-06-04
the service you get through the hole in the wall may be tied to a particular hardware MAC address (e.g. the MAC of whatever you had connected there before) in which case it would likely refuse to provide an IP to the WRT54GL 

there may be an option to clone or spoof the MAC on the WRT54GL, I don't remember (almost certainly there is under DD-WRT), in which case you will need to enter the MAC that your ISP is expecting to see

or you can call your ISP and have them register the current MAC of the WRT54GL

---

### Post by Swanynovin on 2012-06-04
I have reset to factory defaults and change:

[LIST]
[*]DHCP &#8594; PPPoE
[*]Set PPPoE username
[*]Set PPPoE password
[*]Clone mac address of the *good* router (the one that I am using right now)
[/LIST]
It still doesn't work :(.

---

