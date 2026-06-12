---
title: "Getting SSH Tunnel working with my network setup"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by FiReiSFuN on 2009-06-15
Hi all, I'd be grateful for any help you can provide; I think the solution to be fairly simple but it has me stumped.

My network setup is as follows:

We have two networks. Network 1 connects to a VPN at head office; this network includes all of our servers and office computers in a 10.x.x.x range. Network 2 connects to the internet normally, has IPs in the 192.168.0.x range. IPs on both networks are assigned either via DHCP or Static.

I want to be able to sit an Ubuntu server box between the two networks (i.e. have two network cards eth0 and eth1 connected to Network 1 and Network 2) to achieve the following:

Be able to connect to Network 2 from the internet via SSH, and access computers on Network 1. Currently we need to connect to the VPN to achieve this, which is painfully slow.

Any ideas how I could setup Iptables to achieve this?

Thanks for any advice!

---

### Post by superprash2003 on 2009-06-15
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

