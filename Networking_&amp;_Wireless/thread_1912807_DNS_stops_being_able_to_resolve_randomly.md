---
title: "DNS stops being able to resolve randomly"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by DevEight on 2012-01-21
Hi guys!

**Setup**
I recently set up a home network which is having some problems.
The configuration I'm using is the following:
NETGEAR ADSL2+ DG834 which is connected to my ISP using a static IP, DNS and gateway provided by the ISP. I then have 3 computers connected to this router. It's local network is 192.168.0.

There's also another router connected to the NETGEAR, which is a D-Link DI-264 and used mainly for wireless connections. It is set to automatically get an IP-adress, and uses DNS server 192.168.0.1 (the first router). It's local network is 192.168.1.

**Problem**
The problem I'm experiencing is that the devices connected to the wireless router sometimes stop being able to connect to stuff. For example, I might have Skype running, which will keep working fine, but if I want to go to a site it cannot resolve. The devices connected to the first router keep working fine.

**My temporary solution**
It starts working again if I restart both routers, then ping a site using the first router's (the netgear) browser interface to ping a site, then visit that IP using a device which is wireless and connected to the second router. Also, if I try to access the browser interface before restarting the routers, it's unreachable as well.

**What I've tried**
Changing the wireless router's DNS to the static one I got from my ISP

I'd be very helpful for any help!
Thanks in advance.

---

### Post by shymega on 2012-01-22
Hi,

It seems to me that your D-Link router is hosting DNS as well as the Netgear.

This may be the cause of the problem as two different routers are hosting DNS on the same network.

Can you try disabling the DNS on your D-Link router and report back? 

Thanks.

--
sm

---

### Post by knock_ on 2012-01-22
Hi, I had the same problem in my LAN (3 laptops + 2 pc + digital tv  receiver), it was one PC with static IP in conflict with another one with IP from router's DHCP, the router was assigning IP addresses in the order of the PCs were coming into the network. 

The solution was moving to fixed IP numbers for local services and leave free another range of IPs for the DHCPD.

Cheers,

Knock_

---

### Post by DevEight on 2012-01-22
How do I disable DNS in this case? By removing the addresses I wrote in as DNS in the D-Link router? I tried disabling DNS Relay but that made it worse (basically couldn't visit any sites I wasn't already on).

I don't think a IP-address conflict is the problem, as my first router's network is separate from the second's? I took a look at the DHCP-pages of both routers and there doesn't seem to be a conflict.

Thanks for the suggestions so far!

---

### Post by shymega on 2012-01-24
Hi,

Is it possible to use static DNS on your computers instead of DHCP?

Looking at the D-Link manual, I can't see a feature to disable DNS. You could try removing the addresses and seeing what happens?

--
sm

---

### Post by DevEight on 2012-01-30
> **shymega said:**
> Hi,

Is it possible to use static DNS on your computers instead of DHCP?

Looking at the D-Link manual, I can't see a feature to disable DNS. You could try removing the addresses and seeing what happens?

--
sm

Static DHCP is available, not sure about static DNS, though.

I tried removing DNS servers completely from the WAN setup, and browsing through the router still seems to work fine. As the DNS failures aren't all that common I'll be back as soon as another one happens, or in a couple of days.

Thanks for the help!

EDIT: Removing the DNS servers seems to have solved the issue!
Also, how do I tag the thread as solved?

---

