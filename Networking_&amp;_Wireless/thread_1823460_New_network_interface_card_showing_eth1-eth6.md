---
title: "New network interface card showing eth1-eth6"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by creativelies on 2011-08-12
Hi guys.

I've installed a new NIC into our server running Ubuntu Server and rather than showing up as eth0/1/2/etc. it's appeared thusly (output from hwinfo --short):


**eth1-eth6 **           Intel PRO/1000 MT Dual Port Server Adapter
eth6                 Intel PRO/1000 MT Dual Port Server Adapter

Full list:
network:
  eth2                 Intel PRO/1000 PT Quad Port Server Adapter
  eth3                 Intel PRO/1000 PT Quad Port Server Adapter
  eth4                 Intel PRO/1000 PT Quad Port Server Adapter
  eth5                 Intel PRO/1000 PT Quad Port Server Adapter
  eth0                 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller
  eth1-eth6         Intel PRO/1000 MT Dual Port Server Adapter
  eth6                 Intel PRO/1000 MT Dual Port Server Adapter

Why hasn't it appeared as eth1 and eth6? What does "eth1-eth6" mean? No other NIC that we've ever put in the system has done this, and while it could be normal I thought I'd just ask.

I tried searching for this but couldn't find anything.  Any help?

---

