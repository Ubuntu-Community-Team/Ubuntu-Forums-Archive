---
title: "help with home network setup"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by BillyPrefect on 2011-01-24
Hi.

Here's my problem.  I am switching from a DSL to a cable internet supplier.  Cable company only allots 1 or 2 IP addresses.  I have 4 laptops, an HTPC, a torrent box, and a work box.  

I am thinking something along the lines of 

CABLE -> server -> switch -> wired users and wireless AP

I have a box I can mess with with two gigabit NICs.  I was thinking that installing a good server I could get it to supply internal IP's (act as a router) and feed the the switch with some 192. address.  The cable supplies a 67.xxx.xxx.xxx address, which is where I was going to go with two NICs.  Is this a doable thought or am I missing something important?

---

### Post by dBuster on 2011-01-24
> **BillyPrefect said:**
> Hi.

Here's my problem.  I am switching from a DSL to a cable internet supplier.  Cable company only allots 1 or 2 IP addresses.  I have 4 laptops, an HTPC, a torrent box, and a work box.  

I am thinking something along the lines of 

CABLE -> server -> switch -> wired users and wireless AP

I have a box I can mess with with two gigabit NICs.  I was thinking that installing a good server I could get it to supply internal IP's (act as a router) and feed the the switch with some 192. address.  The cable supplies a 67.xxx.xxx.xxx address, which is where I was going to go with two NICs.  Is this a doable thought or am I missing something important?

Okay, why don't you just throw a router in there?  Such as:

CABLE Modem -> Router -> switch if needed

The new wireless routers such as Cisco E2000 and E3000 have gBit ports for wired connections, 4 of them, and they are also wireless capable.  The router can be setup to assign the IP addresses you want it to.  They are also wireless B/G/N capable as well.  I have three laptops, a network printer, Network hard drive (NAS), a DVR connected to the network...  I have no issues with ports or connections.  If you need more than four wired ports then look at adding say an 8 port switch off of the router.

Something to think about.

---

### Post by BillyPrefect on 2011-01-24
I just don't want yet another device. I have spent enough money on my toys, and having the spare PC seems to be begging to be put to good use.

I am reading up now on turning it into a router and a server - possibly.  Just need to work my way through the information.

---

