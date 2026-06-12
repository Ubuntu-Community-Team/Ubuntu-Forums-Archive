---
title: "Using Ubuntu as a router"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by cloyne on 2010-08-28
Hi there,

We have three 20 megabit ADSL2 lines (2 static, one dynamic) which each has its own modem/router. In the house we have a switch that connects to 10 APs throughout the house and numerous LAN lines. We have a server with Ubuntu 10.04 installed.

In the ideal world, we run all three incoming ADSL lines aggregating into the server, bonding them, acting as a router (DHCP, DNS, etc) and sending it to the switch.

We've looked around and haven't found any all-encompassing solutions. What is the best the way to do this? 

In the short run, and if this infeasible, we would still like to accomplish this with only one of the ADSL2 lines, foregoing the bonding.

Thank you so much for any help.

---

### Post by iponeverything on 2010-08-28
bonding is cooperative, the far end equipment has to configured appropriately and near end will have to have the lines terminating on the same box. 

A good solution in your case might be to spread the clients over each outbound.

---

### Post by BkkBonanza on 2010-08-28
You can do this with bonding or with routing tables on an Ubuntu box. You would need an ethernet interface for each adsl modem.

See bonding tutorial here,
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

Also using routing tables method here,
[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

It may even be possible to use the routing method with one interface and a switch on adsl side but I'm not sure about that.

After you have the WAN side done you need to add a few iptables rules for NAT masquerading and routing to the inside. See here, (though I found it simpler than this)
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

You will want something like dnsmasq installed to handle dhcp/dns on internal LANs and wireless if providing that..

I have a small mini-itx box I set up like this as a router. It didn't take long to get it going.

BTW I got one of those Intel Server DUAL 1Gbit LAN cards. They are often on ebay for $10-20 or so. I lucked out at $10 inc shpg.

---

### Post by cloyne on 2010-08-29
Much thanks for the help. Got the routing working and will wait for the dual ethernet card to start the bonding (our mobo only has two pci slots so thanks a lot for that recommendation).

Before we start the bonding, I have two questions...

First, and as I mentioned earlier, our DSL provider gave us two static lines and one DHCP line (I am not sure why). Our network is currently only connected to one of the static lines. Will the DHCP line be tricky to bond with two static ones?

Second, nearly everyone in our house uses the internet to access a university's servers. We have been told that one of the dangers of bonding is that the university's servers will log you off if you are accessing from multiple IPs, meaning that when we do the bonding, we will need to configure it so that each individual client is going through only one of the three modems. Does that mean we should consider the routing table method over bonding? 

Thanks again.

---

### Post by BkkBonanza on 2010-08-29
> **cloyne said:**
> 
First, and as I mentioned earlier, our DSL provider gave us two static lines and one DHCP line (I am not sure why). Our network is currently only connected to one of the static lines. Will the DHCP line be tricky to bond with two static ones?
I don't think so but I've never done that and a look at the docs doesn't really clarify. You may end up using a hybrid of the static ones bonded with the dhcp one via routing tables (though how that will combine with your second question I can't say).

> **cloyne said:**
> 
Second, nearly everyone in our house uses the internet to access a university's servers. We have been told that one of the dangers of bonding is that the university's servers will log you off if you are accessing from multiple IPs, meaning that when we do the bonding, we will need to configure it so that each individual client is going through only one of the three modems. Does that mean we should consider the routing table method over bonding? 
Thanks again.
I think bonding will do that. It has a number of modes to control how the bandwidth is delegated. I think mode 2 sounds suitable for this because each connection should remain stable on one route.

While I have had to use bonding in the past I'm not an expert on all it entails.

---

### Post by cloyne on 2010-09-05
Thanks for the continued help BkkBonaza.

The dual ethernet card just came in the mail so I (rather nervously) am ready to attempt the bonding.

To  clarify, this is how it is set up now: eth0 is connected to a static  dsl modem, eth1 is connected to the switch. I used Firestarter to  connect the two (iptables seemed rather intimidating).

Now I'd  like to add two more lines so it will be: eth0, eth1, and eth2 will each be connected  to a modem. eth0 and eth1 have static ip addresses assigned and eth2 is  dhcp. eth3 will connect to the switch.

So the basic to-do process should be...

 (1) Install and configure ifenslave. Check.

 (2) Edit the /etc/network/interfaces file.

Currently, this file looks something like this:

```
auto eth0
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask xxx.xxx.xxx.xxx
    gateway xxx.xxx.xxx.xxx

auto eth1
iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
```[FONT=Arial]

Following the bonding tutorial, I should change it to something of this nature?:

[/FONT] ```
auto bond0
 iface bond0 inet static
 address 192.168.1.10
 gateway 192.168.1.1
 netmask 255.255.255.0
 slaves eth0 eth1
 bond-mode 2
 bond-miimon 100

auto eth3
iface eth3 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
```And then lastly step (3), I figure out how to configure iptables and all should work? This just seems too easy, and I'm confused as to how ifenslave will know the static IP addresses of the modems as I see no place to enter it. I must be skipping some important step(s)...?

Thanks again.

---

### Post by BkkBonanza on 2010-09-05
Offhand that seems reasonable.

I don't think the bonding needs to know the modem IPs, just as a normal interface doesn't know it's modem's IP. It just send packets out the interface. 

iptables and routing tables both need to be worked out after. I expect it could be complicated. One step at a time. After the interfaces are up see if you can traceroute to google by specifying the interface, **traceroute -i bond0 google.com**. I think that should provide interesting info.

---

### Post by cloyne on 2010-09-06
You say iptables and routing tables both need to be worked out after, but I was under the assumption that using routing tables was an alternative to bonding, not something in addition. What does setting up the routing tables entail?

---

### Post by BkkBonanza on 2010-09-06
The difference is in how the routing is set up. Routing tables for load balancing two interfaces is more involved, for sure, but often you'll have to make some basic routing changes just to get gateways set properly and such. It could all be default or handled well enough by dhcp. 

I don't do this every day and the last time I did was months ago now, so partly I'm just winging it. I can make suggestions but in the end you'll have to test and see how it works out. Even when I do, it involves trial and error.

Are you able to get sensible output from traceroute?

---

### Post by eshwar_andhavarapu on 2010-09-09
keen to try this soon. tried bonding earlier and wasn't a very pleasant experience. but it did give above 2x throughput over lan when 2 interfaces were bonded. but interfaces of the same speed. different speed interfaces make it behave funny.

---

