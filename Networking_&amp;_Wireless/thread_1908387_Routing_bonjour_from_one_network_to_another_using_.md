---
title: "Routing bonjour from one network to another using NAT"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by MadEgg on 2012-01-13
Hi all,

I've got the following setup:

- One /16 network with public IP addresses
- Two /24 networks with private IP addresses (10.0.0.0/24 and 10.0.1.0/24)
- One Ubuntu server connected to all three networks, performing NAT between the public network and the private networks.

On the /16 public subnet, there are some devices (printers mostly) publishing themselves using zeroconf/bonjour.

My question is if there is any way to forward this zeroconf information to the private subnets? My first guess would be to select one private IP on each subnet, for each device that I'd like to forward, and make that act as a mirror for the real device. I found this: [http://ubuntuforums.org/showthread.php?t=1813472](http://ubuntuforums.org/showthread.php?t=1813472) but I suppose there should be some way to do this when you want to explicitly configure for one or more specific evices?

So, something like this: if there is a printer at 1.2.3.4, select a private IP, say, 10.0.0.200, and have all traffic reaching the NAT router, including multicast, from that address be forwarded to the 10.0.0.0/24 range, appearing as if it was sent from 10.0.0.200, and have all traffic to 10.0.0.200 forwarded to IP 1.2.3.4.

Is that a possible solution, or is there an easier solution? And I have no idea how to go about this using iptables or something like that. Thanks for any suggestions!

---

### Post by MadEgg on 2012-01-21
Any ideas?

---

