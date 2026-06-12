---
title: "Wierd Advanced Routing Problem"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by Anquietas on 2012-12-23
Hello,

I have an advanced routing problem here.
I need the advice of a Networking Expert or a CCNA/CCNP level administrator.

The problem can be found here:
[http://hosted.infosky.ro/interesting.png](http://hosted.infosky.ro/interesting.png)

I have changed the IP addresses to simplify the output.

As you've noticed, I have 2 networks: 192.168.0.0/24 and 192.168.1.0/24 linked to the Router.
192.168.0.0 - is an Ethernet Network.
192.168.1.0 - is a Wireless Network.

My Laptop is running Ubuntu Linux and my router is running Gentoo Linux.

I have connected the Laptop to BOTH the 192.168.0.0 net (via eth0) and to 192.168.1.0 net (via eth2).

So my routing table looks like this:
```

default via 192.168.0.1 dev eth0  proto static 
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2  metric 1 
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.2  metric 9

```

The PROBLEM: When I ping the Wireless Interface of the Laptop (192.168.1.2) from the Computer (192.168.0.3) the ping DOESN'T WORK !
It travels the network up to my Wireless NIC on the Laptop but it dies there !

But if I ping the Router Interface for the WLAN (192.168.1.1) from the same machine (192.168.0.3) it works !

Pinging everything else from Laptop also works !

Being connected to 2 networks on my laptop via my physical interfaces, I have at least 2 directly connected routes.
So it's not a routing problem from what I have seen.

If I remain only on wireless and disconnect Ethernet, everything works fine.
The problem only arises when I'm using BOTH the connections at the same time.

I wiresharked my laptop on all interfaces and filtered for ICMP, and when I ping from the Computer to the Wireless Interface of my Laptop I see that the PINGs are indeed coming into my wireless interface !
But my OS does not send replies.
Only ICMP requests, no replies.

Theoretically it should receive PING on wlan interface and send it out on the ethernet interface (since my ethernet network is directly connected trough eht0). - as indicated by my Red directions in the drawing.

So it's a "ping trough one interface, reply trough other" scenario.

Before you ask, my Router is already set to ip_forward=1, beucase my laptop can sense the pings coming on the wlan interface.

Please, only reply if you understand what I am saying here, please do not "BUMP" or other stuff.
I need serious help here.

Thank you !

---

### Post by DangerDevil on 2012-12-23
You should enable routing too on the laptop.

---

### Post by Anquietas on 2012-12-23
I've already done that: IP_FORWARD = 1 on the Laptop.

Still no luck...

---

### Post by DangerDevil on 2012-12-23
OK,
the Laptop gets an ICMP request (on the WLAN-Interface) from an IP-Address directly connected to the LAN-Interface. So it sends the reply through the LAN Interface. Thats normal routing.

You should set metrics and/or use Source-Routing.
Eventually only the ping doesn't work because of the wrong source adress-answer.
Are you able to ssh or http the laptop?

---

### Post by Anquietas on 2012-12-24
Yes I am able to SSH to the Laptop.

Metrics are irrelevant because I'm not using any dynamic routing protocol.
Only Connected Routes and Static Routes.

From what I understand, Source Routing is used for telling the OS where to route some packets that are comming from certain networks.
This is not the case for me.

It SHOULD route the packets trough the eth0 interface (because I already have a directly connected route trough eth0).
No additional routes should be required....

---

### Post by The Cog on 2012-12-24
I suspect that reverse path filtering may be the issue. This prevents processing of packets that arrive on an interface that does not match the route to the sender - packets arriving from an unexpected direction.

cat /proc/sys/net/ipv4/conf/all/rp_filter
if it's set to 1 then reverse path filtering is active. Try this command:
```
sudo -i
echo 0 > /proc/sys/net/ipv4/conf/eth0/rp_filter

```to disable rp filtering on the ethernet interface. Or write 0 to ipv4/conf/all/rp_filter which I think will disable rp-filtering globally.

Edit /etc/sysctl.d/10-network-security.conf to chenge the setting after reboot if this is indeed the problem.

---

### Post by Anquietas on 2012-12-24
Done that, still no luck.
Can't ping from Computer (LAN) to the WLAN Interface of Laptop when Laptop is connected on both networks...

---

### Post by The Cog on 2012-12-24
Does the laptop issue an ARP request for 192.168.0.3 when it gets the ICMP echo request? If so, which interface and which source address does it use? Use wireshark to check.

---

### Post by Anquietas on 2012-12-24
No, it does not perform ARP.

I've checked, the ARP table does not have a record for 192.168.0.3.

When I pinged from 192.168.0.3 to 192.168.1.2, in order to send the ICMP reply, it should have performed an ARP to find out who is 192.168.0.3, but it did not.

Only if I directly pinged 192.168.0.3 from the Laptop the ARP is performed and ping works.

But the reply ping's ARP does not work.

---

