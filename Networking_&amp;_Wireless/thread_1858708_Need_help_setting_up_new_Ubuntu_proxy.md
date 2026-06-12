---
title: "Need help setting up new Ubuntu proxy"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by dweitzel on 2011-10-12
Sorry for being so Ubuntu ignorant, but maybe you can get me started.

I have a Dell 2300 installed with the latest Ubuntu up and running with 2 ethernet cards installed and recognized.

I want this server to act as a proxy server from a DSL modem on Eth0 and route the traffic to Eth1 which will have a Linksys WRT54G running DD-wrt on it. The Linksys will have 1 or 2 hardwired PC's on it and also route wireless traffic to and from Eth1.

What I need are step by step directions or a link to the appropriate web pages so I know how to assign the addresses to Eth0 and Eth1, possibly run DHCP on the Ubuntu machine, and keep the Linksys at its default address and service the routing functions of wireless and the hard wired machines.

Do I want to do this through the GUI interface or should I be doing this through the command prompt?

I think I eventually want to run something like squid on the Ubuntu machine so I can block sites like runescape and facebook selectively and certain HTTPS sites by domain name.

Can someone give me very simple steps or page links to setting up Eth0 and Eth1 so this machine will route traffic from my internet provider to the Linksys wireless router?

Thanks. Sorry if this is so beginner. Just need a kick in the right direction.

DW

---

### Post by collisionystm on 2011-10-12
> **dweitzel said:**
> Sorry for being so Ubuntu ignorant, but maybe you can get me started.

I have a Dell 2300 installed with the latest Ubuntu up and running with 2 ethernet cards installed and recognized.

I want this server to act as a proxy server from a DSL modem on Eth0 and route the traffic to Eth1 which will have a Linksys WRT54G running DD-wrt on it. The Linksys will have 1 or 2 hardwired PC's on it and also route wireless traffic to and from Eth1.

What I need are step by step directions or a link to the appropriate web pages so I know how to assign the addresses to Eth0 and Eth1, possibly run DHCP on the Ubuntu machine, and keep the Linksys at its default address and service the routing functions of wireless and the hard wired machines.

Do I want to do this through the GUI interface or should I be doing this through the command prompt?

I think I eventually want to run something like squid on the Ubuntu machine so I can block sites like runescape and facebook selectively and certain HTTPS sites by domain name.

Can someone give me very simple steps or page links to setting up Eth0 and Eth1 so this machine will route traffic from my internet provider to the Linksys wireless router?

Thanks. Sorry if this is so beginner. Just need a kick in the right direction.

DW


If this a brand new server and you want SIMPLE.

Use Zentyal.

See my signature.

Its based on Ubuntu 10.04.

---

### Post by dweitzel on 2011-10-13
Ok, I've found the Eth0 and Eth1 setup pages. I assume that I want to let Dhcp run on Eth0 which will receive a ip address and nameserver from my DSL provider. I then assume that I need to set up a routing statement to Eth1. I need step by step help to set the ip address on Eth1 so that it is on the same subnet as my linksys wrt54g and Eth1 can act as a gateway to Eth0 as a passthrough for the internet.

Any help would be appreciated.

Dw

---

