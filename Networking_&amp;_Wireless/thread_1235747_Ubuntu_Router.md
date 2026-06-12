---
title: "Ubuntu Router"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by Reirol on 2009-08-09
Hey, I'm looking to build an Ubuntu Server. The problem is that there are two routers on my network, creating two different Local IP addresses. This becomes problematic because regardless of which router I attach my Ubuntu box to, some of the computers are unable to reach it and it's files. 

Is it possible to set up the Ubuntu box as the main router and make the rest of the routers slaves? Such that everyone would be sharing the server's internet connections, therefore making the routers simply gateways?

If so, how to I go about doing such a thing. I have a couple 100mbps Ethernet cards lying around in one of these motherboard boxes if I need more than one.

Enjoying the Coffee,
Reirol

---

### Post by aesis05401 on 2009-08-09
First thing to do is configure the networking stack and iptables rules on your server.  The networking stack is manipulated by writing 0/1 to particular files for the purpose of turning various network functionality off/on.  

The iptables rules handle the packets that actually hit the server.  Packets can be forwarded, modified, dropped, logged, etc.  

This overview is a good starting point for iptables:[http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

This script sample should give you a good starting point for writing a custom config:[http://www.novell.com/coolsolutions/feature/18139.html]("http://www.novell.com/coolsolutions/feature/18139.html")

With these packages configured properly you can use your Ubuntu server as not only the master routing authority on your LAN, but as a perimeter defense device. Good luck.

Edit: Starting with two nics is easiest IMO.  Configure one to face the WAN and one to face the LAN.  The forwarding between cards will be handled in your iptables rules.

---

### Post by AmerNewbieInDE on 2009-08-09
well, i am still a noob with linux, but networking is networking... it mainly depends on the routers that you have. what you want is a switch connected to your server then to your pc`s and your server connected to internet through a firewall.. but, with your 2 routers, it might be possible to connect to your server, if you turn off dhcp on the router, assign dhcp to your server, or just assign each pc on your network an ip and you dont need dhcp. but obviously if you connect your routers to the server, you need more then one nic on the server..

---

### Post by aesis05401 on 2009-08-09
> **AmerNewbieInDE said:**
> *snip* ..but obviously if you connect your routers to the server, you need more then one nic on the server..

Not necessarily.  You can keep the router traffic separate even while daisy chaining them by using two subnets and placing a forwarding rule on the router nearest the server. 

This way there would be only one cable to the server.  This can be accomplished with only one nic in the server if you are willing to spare the overhead to run virtualized networking interfaces and have all traffic running over a single ethernet cable.

Either way, if the OP has additional network cards the task is simplified.

---

### Post by AmerNewbieInDE on 2009-08-09
daisychain would work, but not with two networks like he said... unless one of the routers were made to do that but i havent seen a router able....

---

### Post by aesis05401 on 2009-08-09
> **AmerNewbieInDE said:**
> daisychain would work, but not with two networks like he said... unless one of the routers were made to do that but i havent seen a router able....

I am running with two different LAN subnets on two different routers connected to one server via daisychain.  If you add in my virtual subnets there are days when I am running five distinct network segments on the same LAN through a combination of two ethernet routers, one wireless access point, and one firewall/server.

It is not difficult.  All the commercial routers available these days have NAT/port forwarding/filtering ability, and the server can be set up in any number of manners to allow this to happen.  The difficult part is just deciding which methods work best for you.

---

### Post by AmerNewbieInDE on 2009-08-09
well, i am not argueing with you, but this person said, they are thinking of adding a serve, they have two routers, and can it be done with what he has...with that informaion, he is not sure what he is doing (because mainly he is asking) so, ok, as you sate, yes it can be done.. but i dont know if it can be done with what he has for equipment. not to mention knowlege to do it all...

---

### Post by Adina on 2009-08-10
when you have machines behind 2 different routers and want them to communicate with eachother you need to make a static route so the router knows where to send the packets. (a subnet behind another router is not automaticly added to the default route on the router you are behind)

---

