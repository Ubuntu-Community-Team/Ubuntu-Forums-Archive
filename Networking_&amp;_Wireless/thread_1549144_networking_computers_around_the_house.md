---
title: "networking computers around the house"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by ak123 on 2010-08-09
to start, im going to make a little key

these are the computers in my house
ml         - my laptop           - ubuntu nbr
md         - my desktop          - ubuntu desktop
bd         - brother's desktop   - windows XP
dl         - dads laptop         - windows XP
sl         - mom's laptop        - windows vista (might upgrade)
sd         - mom's desktop       - windows XP

here are the two routers in the house and systems connected
_Network A _
ml -wireless
md -ethernet cable
bd -wireless 
sl -wireless

_Network B_
dl -wireless
sd -ethernet cable

so now here is the problem..

we want to connect every computer with these routers.. the things that i want from this are: file sharing, 
                           prints using the printer connected to                     sd..

so far, ive connected ml and md successfully using ssh.. however, what i want to know how to do is set up the rest of the connections..

---

### Post by YesWeCan on 2010-08-09
Hi. Would you elaborate a little?
The two routers are wireless. Are they connected to different cable modems...or is one router connected to the other?


Sharing files between the linux PCs using SSH will not be a problem but sharing files between Windows PCs on different subnets will be.
[http://www.dslreports.com/forum/r21797165-Windows-Vista-file-sharing-across-2-local-subnets](http://www.dslreports.com/forum/r21797165-Windows-Vista-file-sharing-across-2-local-subnets)

How much do you know about Windows networking?
There are at least 3 ways I can think of off the top of my head:
1. Research how to do Windows networking across subnets. I am no expert but it may involve configuring a domain master and local masters.
2. Avoid the problem by putting all PCs and printers on the same subnet. By far the least technical effort.
3. Cheat by using a VPN tunnel to merge the two subnets in a virtual manner. OpenVPN will do this.

---

### Post by ak123 on 2010-08-09
no... they are both separate router-cum-modems... No.. it is not possible to put them all on the same subnet... and i also am starting to wonder if they are even on the same line because they both have different plans...

---

### Post by lukeiamyourfather on 2010-08-09
So you have two internet connections and two routers in the same place? Weird. I would suggest getting a dual WAN router.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122213&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Network+-+Firewalls-_-Netgear+Inc.-_-33122213](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122213&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Network+-+Firewalls-_-Netgear+Inc.-_-33122213)

Alternatively you could disable the DHCP server on one of the routers you already have and then set the default gateway on each machine manually so they use whatever internet connection you specify. Then plug both routers into a main switch that everything else is connected to. Though I think you'll have better luck with the dual WAN router.

---

### Post by lukeiamyourfather on 2010-08-09
Better yet, ditch one ISP and buy a switch. One fast connection is more useful and cheaper than two slow connections.

---

### Post by YesWeCan on 2010-08-09
Luke's right if your family don't mind having all PCs on the same network and using a common router.

I'm guessing but I suppose your parents might want to have a separate internet connection from you and your brother. So they probably won't want to put all PCs on the same network and router.

In this case you can still do what you want but you need more knowledge. I don't know much about windows networking so I do not know whether there is a built-in Microsoft method to allow the Windows PCs on network A to see the Windows PCs on network B across routers. I do know how to do this using OpenVPN. I suggest you Google for how to do Windows networking across different networks and/or find a Windows forum to ask about this first. :)

---

### Post by YesWeCan on 2010-08-09
I am happy to guide you on OpenVPN but it is not trivial. I know that Windows has its own version of VPN that you may be able to use. In short, you create a "virtual" connection between 2 PCs, one on each network. These 2 PCs then "show" the remote PCs on their own network. In any case, you would need to install VPN or activate VPN on one of your parents PCs on network B...or...you need to add another PC to network B to run the VPN. I imagine the folks would prefer you not to install things on their PCs.

---

### Post by YesWeCan on 2010-08-09
A simpler idea!
Add a wireless interface to sd (a wireless usb stick, for example), the wireless connecting to the router on network A. So sd now has a wired connection to network B and a wireless connection to network A. Network A should then be able to see sd and the printer on sd. I am not sure whether network A would also be able to see dl: you would have to tell sd to bridge its two interfaces or something like that (in Windows Network Manager). But you would be able to use the printer.

---

### Post by ak123 on 2010-08-09
thanks for all the responses.. both routers are on the same ISP... they gave us two connections because network A was getting clogged up... so i think VPN might be a good idea.. but id need some help with it..

---

### Post by ak123 on 2010-08-12
bump

---

