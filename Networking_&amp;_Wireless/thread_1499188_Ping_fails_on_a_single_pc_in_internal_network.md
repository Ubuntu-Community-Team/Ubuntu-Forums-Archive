---
title: "Ping fails on a single pc in internal network"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Sempfinger on 2010-06-01
Hello everyone,

I want to ssh to a pc in our home network. It is a standard network in terms of a DSL router, dynamic IPs via DHCP, WPA2/PSK security, wireless network connection for all pcs except one which is wired to the router.

I got the error "no route to host" from ssh. Openssh-server was already installed. It turned out later that the laptop I want to ssh to (namely the one which is connected by cable) cannot be pinged by any other laptop on the network.

The pc in question (lucid lynx with most recent updates) is online, can ping itself and the router, but cannot ping others in the network and cannot be pinged by them. I suspect a firewall setting of being the problem...

I hope I made myself clear. I appreciate any hints on diagnosis tools and / or configuration. If you need more info, please let me know.

Thanks in advance!

---

### Post by Iowan on 2010-06-01
Does the "problem child" have static or DHCP address. If it were a routing problem, one wouldn't expect to ping the router.

On the other hand... If routing is messed up on the router and everything goes out the wireless port...

---

