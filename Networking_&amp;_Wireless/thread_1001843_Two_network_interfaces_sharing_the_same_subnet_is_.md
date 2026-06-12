---
title: "Two network interfaces sharing the same subnet: is it OK?"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by wirawan0 on 2008-12-04
OK guys... here is a simple networking quiz. I don't know the answer though.

I have two network (ethernet) interfaces on my laptop: eth0 is a wired network, and eth1 is a wireless (on one laptop, it is ipw2200; on the other one it is a PCMCIA card with 3com card [atmel chipset]). They are used alternatively to connect to a router at my home, which has address 192.168.0.1. The IP addresses are:

eth0:  192.168.0.176
eth1:  192.168.0.177

Both have the same gateway and subnet. Here's the complete routing:

```

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1

```

Here's my question: **Is this a valid configuration, when the cards are on (up) simultaneously?** I found out that this causes a test ping (e.g. ping 192.168.0.1) to receiving answer when I brought up the two network cards up.

FYI: I am using Ubuntu 8.10, and NetworkManager is up. It seems to me that it does not matter whether NetworkManager is up or down; the problem is still there.

Wirawan

---

### Post by puppywhacker on 2008-12-04
hi,

It is a valid routing case, asynchronous routing is perfectly fine

The order in the routing table will decide which interface is used. in your example the eth1 will be used for every host in 192.168.0.X while eth0 will be used as default route. eth1 will not be used as default route. 

There is however one exception and that is the rp_filter which drops all traffic which is routed asynchronously.

To use both of your interfaces at the same time you have to trunk (bond) them together, but that is dependent on the equipment as it is not a standardized.

You could use traffic shaping to make intelligent routing cases.

---

### Post by Iowan on 2008-12-05
My understanding (often mistaken) is that two NICS in the same subnet does not work well - plays havoc with routing. As suggested, I keep finding new ways to be wrong. ;)

---

### Post by jmoorse on 2008-12-07
Assuming this is the same LAN segment you may have problems when traffic received on eth0 is sent as return traffic with src eth1.  The receiving machine may see this as unsolicited traffic and drop it.  In the case of sending traffic between a stateful firewall, this will always be the case

---

