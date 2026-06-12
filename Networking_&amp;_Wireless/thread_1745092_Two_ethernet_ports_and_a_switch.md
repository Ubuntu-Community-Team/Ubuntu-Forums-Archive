---
title: "Two ethernet ports and a switch"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Sillywombat on 2011-04-30
Okay, not really a ubuntu specific question, but here we go.
Just recently got a new rig, and was wondering, is there a way to share internet via a switch. I understand the problems with switches is that they dont assign IPs like routers do, but if my ubuntu machine worked like a router by assigning IPs, could it work?

Current setup is as such.
I have one ubuntu machine with 1 ethernet port (this shall be the main preferably)
1 mac with a single ethernet port
1 modem with a single ethernet port that cannot assign more than one IP address.
And a 5 port switch.

Would it be possible to place the modem into the switch, get the ubuntu machine to receive the IP address, and broadcast all other address' to everyone else via the same switch and ethernet cable?

Any help on this would be great, even if its to tell me its a silly crackpot idea.

---

### Post by JackRabid on 2011-05-01
It might be possible- but I really don't think it is.

Either get a proper router or get a second NIC and look into setting up an ubuntu box as a 2 interface firewall/router- tons of tut's if you just search.

Personally I'd just get a router and be done with it

---

### Post by Cheesehead on 2011-05-01
Yeah, you can do it...but be ready for tough troubleshooting.

Set up two networks. Lets's call them 192.168.1.* and 192.168.2.*
One network connects only the modem and your Ubuntu machine (router).
The second network connects the Ubuntu machine (router) to your other local machines.

Trick #1: Do a search for **binding** (not bonding or bridging) two IPs to the same NIC. One IP on each network, running through the same ethernet jack.

Trick #2: Both networks run over the same wires, and both run through the switch. (This really confuses some people). Each machine sees two separate networks - based on the IPs, but human eyes see only one twisty mass of cables all hubbing together at the switch.

1) Set up Network #1.  Modem -- Switch -- Ubuntu Machine (router)
    This is probably really close to what you already have now.

2) Set up the Ubuntu Machine to actually be a router. That means: 
    Changing the kernel IP Forwarding flags,
    Setting up the IPTables for NAT (and any other firewall activity),
    Installing dnsmaq for NAT and DHCP of the second network,
    Editing /etc/network/interfaces to define the two bound interfaces.

3) Set up Network #2. Since the router is up, and the Switch -- Router cable is already in place, that just means connect the switch to the other machines.

Lots of testing and troubleshooting involved, of course.

Good luck!

---

### Post by collisionystm on 2011-05-01
> **Sillywombat said:**
> Okay, not really a ubuntu specific question, but here we go.
Just recently got a new rig, and was wondering, is there a way to share internet via a switch. I understand the problems with switches is that they dont assign IPs like routers do, but if my ubuntu machine worked like a router by assigning IPs, could it work?

Current setup is as such.
I have one ubuntu machine with 1 ethernet port (this shall be the main preferably)
1 mac with a single ethernet port
1 modem with a single ethernet port that cannot assign more than one IP address.
And a 5 port switch.

Would it be possible to place the modem into the switch, get the ubuntu machine to receive the IP address, and broadcast all other address' to everyone else via the same switch and ethernet cable?

Any help on this would be great, even if its to tell me its a silly crackpot idea.

Very possible and very easy.
first, you need to find out if your isp is handing dhcp or the same ip everytime. You will need a static address from your isp.

All you need is dhcp3 server and a good how to.

Give your ubuntu machine the static ip from your isp. Add the dns info gateway...etc. install dhcp3-server from the repo's

Google for configuring a virtual ip on ubuntu. Your virtual ip will be 192.168.1.1. So now your ubuntu has the external address and the internal.

You can now setup dhcp3 to hand out the proper information automatically or statically assign your home computers to use ubuntu as their gateway and your isp dns servers. And give them a 192.168.1.xix address. The. 1 being the gateway. Im on a phone so I can't provide alot of info, but yes its possible. Just google for the keywords.

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

