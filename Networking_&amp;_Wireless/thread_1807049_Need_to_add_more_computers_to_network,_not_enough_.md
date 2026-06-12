---
title: "Need to add more computers to network, not enough Ethernet ports"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by Antarctica32 on 2011-07-18
I just cleaned out my basement and I want to put some of my computers down there, with a wired gigabit (10/100/1000) internet connection. I don't really know a lot about networking so please bare with me. Let me first explain my setup: I have a Motorola SB5120 modem that has a cable port, a USB port, and a single ethernet port. Out of the ethernet port it connects to my new Linksys e3000 gigabit Wireless-N router that has 4 ethernets not counting the uplink. Right now I have computers connected to all 4 of those 10/100/1000 ports, but if I somehow got ethernet down in my basement a couple of those computers would go down there. I really want to add more ports somehow and not just stretch an ethernet cable from my router to downstairs, that way I will still have open ethernets upstairs as well. I did find a coax cable downstairs that is probably connected. Would it be possible to get an entirely new modem and router and basically create a whole new network? Would that even be realistic if possible, compared to other options if any? Would it be possible to connect an ethernet switch like this one:
 [http://www.microcenter.com/single_product_results.phtml?product_id=0334608]("http://www.microcenter.com/single_product_results.phtml?product_id=0334608")
to my router via ethernet, put the switch downstairs, and instantly have 10/100/1000 down there? Could I do the same with a different router instead of a switch? 
All help of any kind is greatly appreciated, thanks in advance.

---

### Post by jmoorse on 2011-07-18
You might want to look into powerline, I have this kit at home:

[http://goo.gl/DO3nt](http://goo.gl/DO3nt)

It works just fine for me.  I get about 93mbps but that is more than fine for home use.

---

### Post by Antarctica32 on 2011-07-18
> **jmoorse said:**
> You might want to look into powerline, I have this kit at home:

[http://goo.gl/DO3nt](http://goo.gl/DO3nt)

It works just fine for me.  I get about 93mbps but that is more than fine for home use.

Sounds like a good idea but is a little too expensive. Also The reason I am trying to get ethernet down there is because it is faster than wifi and I really need a good internet connection for the stuff I do. thanks a lot though. I created this map of my current network, it should be attached to the post.

---

### Post by jmoorse on 2011-07-18
Ok, if you really need the speed run an ethernet cable down to the basement and install another Gigabit switch.  You can get a cheap TrendNet Gig switch for peanuts at frys / etc.

---

### Post by oldfred on 2011-07-18
I have not paid attention since I retired. Switches are a lot cheaper now-a-days. I think I paid that for a cheap hub which just allows multiple connections to one wire but performance is not as good as with a switch.

[http://www.webopedia.com/DidYouKnow/Hardware_Software/2006/router_switch_hub.asp](http://www.webopedia.com/DidYouKnow/Hardware_Software/2006/router_switch_hub.asp)
[http://en.wikipedia.org/wiki/Ethernet_hub](http://en.wikipedia.org/wiki/Ethernet_hub)

---

### Post by jmoorse on 2011-07-18
Yeah I know, prices have really come down.  I don't even think you can buy hubs anymore.  Also 1Gig hubs shouldn't exist, IEEE standards mandate 1000Mbit as Full Duplex only :)

---

### Post by Antarctica32 on 2011-07-18
Ok so your saying that the attached diagram of a setup would work right out of the box? Also would using another router instead of a switch also work?

---

### Post by jmoorse on 2011-07-18
Use a switch, not a router.  Yes that will work fine out of the box.

Added bonus: switches are cheaper than routers.  If you have a Gigabit router laying around I can walk you through how to configure it to work like a switch to save you the cost of buying another device.

---

### Post by Antarctica32 on 2011-07-18
> **jmoorse said:**
> Use a switch, not a router.  Yes that will work fine out of the box.

Added bonus: switches are cheaper than routers.  If you have a Gigabit router laying around I can walk you through how to configure it to work like a switch to save you the cost of buying another device.

Well the thing is i kept my old router when I got my e3000. only problem is its only 10/100. If i was to set it up like that, then it would be only slightly faster than wifi..... 
ok sure show me how. how long will this take? I have to go to swim practice in an hour.

---

### Post by jmoorse on 2011-07-18
A gigabit switch would be better, but the process for the router is as follows: 

Disable the DHCP server and disable wifi in the router-to-become-a-switch's web interface and only use the LAN ports.  Put tape or something over the WAN port (should be yellow).  You should also change the e3000's IP address to be something on your subnet that is not being used.  If it is the same as your current gigabit router, bad things will happen.

Run one cable from gig router to new router-aka-switch and plug computers into the other ports.

---

### Post by Antarctica32 on 2011-07-18
Ok, well I called my dad (who works with computers) and asked if he had a switch so I didn't have to do anything. He said that he did have a Netgear EN104 ethernet hub. Would this work just like a switch would? I researched the en104 (its really old) and apparently it isn't gigibit and it may not even be 100, lawl. Hes going to bring it home with him today, So i'll see then. I don't want to mess with a router if I may have a perfectly good switch/hub thing in a couple hours. I did a little research and found out that the only real difference between a hub and switch is that in a hub you can see the data other computers get and send. Does this really mean anything? or is that like a huge problem? I don't really care if other computers can see what another one does cuz there all in my house and stuff.

---

### Post by jmoorse on 2011-07-18
You would get better performance with Wifi than with a 10mbps hub.  I encourage you to read up on the difference between a hub and a switch

Use the router-aka-switch or buy a cheap 1Gig switch, you can find them for ~$20 in some places.

[http://goo.gl/G17zF](http://goo.gl/G17zF)

especially if:

> 
I really need a good internet connection for the stuff I do


---

### Post by Antarctica32 on 2011-07-18
> **jmoorse said:**
> You would get better performance with Wifi than with a 10mbps hub.  I encourage you to read up on the difference between a hub and a switch

Use the router-aka-switch or buy a cheap 1Gig switch, you can find them for ~$20 in some places.

[http://goo.gl/G17zF](http://goo.gl/G17zF)

especially if:

Yeah, was thinking the same thing: if its 10mb/s than I should just use wifi. But the thing is it could very well be 100. Anyway, I will probably just get a gigabit switch from a local computer store. I already went on there website, they have one for $20

---

