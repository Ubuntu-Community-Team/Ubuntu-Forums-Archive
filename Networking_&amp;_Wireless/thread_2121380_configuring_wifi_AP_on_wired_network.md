---
title: "configuring wifi AP on wired network"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by marquee moon on 2013-03-01
hello, 
Using 12.04, I currently have a wired network with a wireless router in-line, like so: 
[ATTACH=CONFIG]239589[/ATTACH]
But I need to have the wireless router closer to where I use wireless devices, so I'm trying to put the wireless router onto the wired network as a 'spur', like so: 
[ATTACH=CONFIG]239588[/ATTACH]

I'm aware that I need to configure the wireless router (Cisco Linksys E1000) to act as an AP. 

To start with, I re-set everything. After re-setting, my computer recognises the wireless network. 
I can then  connect to the wireless router's setup page either via wired or wireless link to configure as an AP. 

I configure as follows: 

ensure DHCP server is enabled on the original modem/wired router.
disable DHCP server on wireless router
set the LAN IP address of the wireless router to 192.168.1.66 (dynamic IP range for modem / wired router is 192.168.1.1>65)
ensure subnet mask address is same for wired & wireless routers
disable UPnP & firewall on wireless router

But when I change the IP address of the wireless router, I loose the connection (both wired & wireless.)

What am I doing wrong? This should be so simple, but I've been at it for 5 hours now!

---

### Post by steeldriver on 2013-03-01
I've done exactly that config in the past - albeit with a Linksys WRT54GL as the AP and a Speedtouch DSL modem/router

The secret iirc is to connect from a LAN port on the main router to a LAN port on the "AP" (NOT the WAN port) - that way it essentially just works as a dumb switch

Everything else you're doing sounds right

---

### Post by marquee moon on 2013-03-01
ahhhh.....thanks, Steeldriver! 
 I have the AP connected on the WAN port at present. Will try on the LAN port when I get a chance (there's a baby sleeping in the room at the moment!)

Edit... just done it, and it works! thanks again, Steeldriver.

---

