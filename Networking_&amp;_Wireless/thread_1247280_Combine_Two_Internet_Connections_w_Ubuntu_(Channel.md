---
title: "Combine Two Internet Connections w/ Ubuntu? (Channel Bonding / Link Aggregation)"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by Sootah on 2009-08-22
My house is networked with our neighbors. Currently I have a 10Mbps cable internet connection, and they have a DSL connection through Qwest of unknown speed.

What I'd like to do while they still have the DSL connection, is to use Linux (or any other method, for that matter) to aggregate the bandwidth available in the two connections into one über-connection. I know that you can do channel bonding with Linux, but I have no idea how to set it up; the the couple of things I found for Ubuntu on the subject are old.

Also, both connections are avail when plugged into my hub. SO - can we use just one NIC to do this? Setup a couple of virtual NICs, perhaps? One that'd be on the Baja network subnet, the other on the QWest, and then the computers that want to use the aggregated connection would use the fancy-schmancy Ubuntu system as their gateway. This Ubuntu gateway would then balance the data load across both connections so that we'd end up with a single, faster connection.

Hopefully I explained myself well enough.

Thanks for any and all help!

-Sootah

---

### Post by RobDurdle.com on 2009-09-07
I really want to do this as well, I have 2 different 10mbit connections with 2 independant cable modems, and want to make one super fast 20mbit connection, any tips?

> **Sootah said:**
> My house is networked with our neighbors. Currently I have a 10Mbps cable internet connection, and they have a DSL connection through Qwest of unknown speed.

What I'd like to do while they still have the DSL connection, is to use Linux (or any other method, for that matter) to aggregate the bandwidth available in the two connections into one über-connection. I know that you can do channel bonding with Linux, but I have no idea how to set it up; the the couple of things I found for Ubuntu on the subject are old.

Also, both connections are avail when plugged into my hub. SO - can we use just one NIC to do this? Setup a couple of virtual NICs, perhaps? One that'd be on the Baja network subnet, the other on the QWest, and then the computers that want to use the aggregated connection would use the fancy-schmancy Ubuntu system as their gateway. This Ubuntu gateway would then balance the data load across both connections so that we'd end up with a single, faster connection.

Hopefully I explained myself well enough.

Thanks for any and all help!

-Sootah

---

### Post by Gweniviere on 2009-10-09
I too would like to know if this is possible. My company has a DSL line rated at 3.0MB up and 640KB down and a couple of bonded T1s for a 3.0 up and down. Both are from the same provider, however the IPs, netmasks, gateways, etc are different. 

I've read about bonding the nics with ifenslave but it seems to me that would only work if the DSL and the T1s shared a subnet (which they don't). Am I right in my assumption? Or would ifenslave work? And if not, is there something that will do what I am hoping to do?

---

### Post by Iowan on 2009-10-09
[Here]("https://help.ubuntu.com/community/UbuntuBonding") is a help page for bonding... maybe you've already seen it.

---

### Post by FeraTech on 2009-12-11
The linked wiki is for bonding two network interfaces with the same internet connection. Not for bonding two internet connections.

I read through and there is a lot of confusion between the subject.

Link Aggregation/Bonding - combining two network cards on the same connection to increase throughput and have a fail-safe in case one fails

Load Balancing - having two different internet connections and allowing the computer to create new connections alternately using each connection

---

### Post by gregkane on 2010-01-21
I was poking around looking for the best advise on bonding a 2 NICs and I saw this thread. I am a real newbie on Linux but I just wanted to give a word of caution here.

It is one thing to bond 2 connections to the same local ip network (VLAN, segment, what ever) or even to the same internet provider but it is another to try and have a single connection to 2 different internet providers. This is because the path packets would take (and the latency involved) would usually be very different between the two. It would be possible to set up a class of traffic or perhaps a specific connection to one or the other but to try and bond both together as a single pipe would probably not be possible.

Good Luck

---

### Post by jrssystemsnet on 2010-03-23
This is not an easy task, and I don't know of any FOSS that does it simply (or, truth be told, at all).

However, there are quite a few relatively inexpensive multi-WAN routers out there.  I used to use a [Xincom Twin WAN router](http://www.amazon.com/Xincom-XC-DPG502-Twin-WAN-Router/dp/B00022PTV6) and it worked great; somewhat more expensively, Netgear's ProSafe line now carries some multi-WAN routers (haven't personally used any of those, but I like the rest of the ProSafe gear for the price).

---

### Post by tekoholix on 2010-04-07
Take a look @ ebox-platform.com...  Packages are available, and while still in less than perfect state, I've been using it for quite some time.  As well, zeroshell and pfsense, ALL FOSS...

---

### Post by aussie_ on 2010-05-03
I have not used ubuntu as yet and I am doing some research into it but I do know there is a product that will BOND multiple ISP's and it dosn't require any co-opperation from the ISP's. It can do it with the same ISP or different ISP's.
:arrow: [[COLOR=#444444]www.frdmnetworks.com[/COLOR]]("http://www.frdmnetworks.com/") is the site. I spoke to a guy there called Jared and he was full of information and had a great knowledge of the ability to bond and how it compared to a load balancer. I had a great discussion with him about this. I would sugest contacting them as they may be able to assist you.

---

### Post by Alex_L33 on 2010-05-06
perhaps this is a silly idea, but if somebody on here were to own such a Netgear multi-WAN router, and seeing as Netgear's routers run linux with iptables etc, it should surely be possible to telnet into the router and take a look at how netgear did it? (unless I am mistaken - the entire root filesystem can be viewed from the built-in ash shell)

---

### Post by zsa on 2011-02-09
gregkane-
I saw a press release about a company called Mushroom Networks that can actually bond. (They're not load balancing.) They actually can split a request over multiple connections from different providers as well. Apparently they have figured out a way to account for the different latencies of the different IP sources. The press release was about a wireless version, actually. I think it was called Portabella. Does anyone know anything about this product?

---

### Post by Replica2009 on 2011-06-24
Yes, indeed Gregkane. We have been a Mushroom Networks client for a little over 4 years now. We have one of their truffle internet bonding products in our network and it truly bonds the 3 Internet connections we have (T1, DSL and later we added a comcast cable). We never had a single day of Internet downtime in the last 4 years and speeds we get are amazing. They are some some smart phd folks over there who have figured this out, kudos to them...

---

### Post by jpl888 on 2011-10-03
For any of you guys that want to do this yourselves, I did a very non-verbose how to in August see [http://johnlewis.ie/bonding-teaming-internet-connections/](http://johnlewis.ie/bonding-teaming-internet-connections/)

Basically you need an Ubuntu/Debian machine at home and a cheap dedicated/VPS on the net somewhere. It uses Vtun and multi-link PPP to aggregate the bandwidth. I'd be interested in feedback?

---

### Post by bhb192 on 2011-11-12
This is almost what I've been looking for, jpl. The only thing that I don't understand is, why is it necessary to pay for VPN service out in cyberspace somewhere? Couldn't we just run all of that on our own machines? 

This seems like such a simple idea. My 3G service is faster than my actual internet is most of the time so it'd be really cool to just be able to plug in my smartphone when I need the extra bandwidth.

---

### Post by jpl888 on 2011-11-12
Who said you have to pay for a VPN? You need to have a machine on the net somewhere. Rent a Dedicated server or VPS , that's all.

It uses Vtun and multi-link PPP, I tried it with straight bonding, but that doesn't seem to deal very well with links that have wildly variable latency ...

---

