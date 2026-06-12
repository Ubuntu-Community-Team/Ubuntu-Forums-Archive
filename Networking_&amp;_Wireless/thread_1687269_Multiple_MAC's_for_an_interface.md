---
title: "Multiple MAC's for an interface"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Jeroen1000 on 2011-02-13
Hi everyone,

My ISP (cable internet) hands out DHCP in the 10.x.x.x/something range for their digital TV setup boxes. For consumer gear (computers, routers,...) the ISP hands out DHCP in another range.

At this point I would need to put a switch between the cable modem and my router, in order for the setup box to get the correct IP. 
Futhermore, I would need to pull a seperate CAT5E cable to that switch for the cable box. 

That's too much hassle, so what did I do instead: I cloned the setup box MAC-address to the routers WAN interface. I got a 10.x.x.x/something IP and the setup box was quite happy.

Too bad no computer could reach the internet. So that same WAN interface should ask DHCP again, but this time with its real MAC address instead of the cloned one from the setup box.

My router is based on Linux so I was wondering whether what I'm suggesting is possible?

---

