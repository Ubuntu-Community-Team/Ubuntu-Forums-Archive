---
title: "Config 2 Network Cards"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by csbonito on 2012-12-17
hello Ubuntu Community

I'm having a problem I installed a New Ubuntu Server 12.04 with 2 network cards, One with a static public address and one with a private address.

#public
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask 255.255.255.248
    gateway xxx.xxx.xxx.xxx
    dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx  

#intern
iface eth1 inet static
    address 192.168.10.9
    netmask 255.255.255.0
    gateway 192.168.10.4
    dns-nameservers 192.168.3.4
    dns-search example.com


I have internet, access with the Public IP.
The problem is that I cant do ping to another network (ex. 192.168.15.1) but I can to my computer or inside the 192.168.10.0 network, either can't do ping from another network to my server.

I really don't know the whats the problem, maybe someone can help Pls.

Thank you

---

### Post by chadk5utc on 2012-12-17
Do you have a firewall? and do you have routing setup?

---

### Post by csbonito on 2012-12-17
> **chadk5utc said:**
> Do you have a firewall? and do you have routing setup?

No firewall and the the routing works good,

The other thing is that when I diseable the eth0 then I dont have the problem anymore, I can see my server from anywhere, so I think theres a conflict with eth0 and eth1 at the same time.

---

### Post by Doug S on 2012-12-17
What you have described and detailed is how I would expect your system to work.
You can not ping 192.168.15.1 because it is not in your LAN, which is only 192.168.10.0-192.168.10.255. You might need a netmask that includes a larger address space (maybe 255.255.0.0) or add some specific routing (as chadk5utc mentioned). You would have to supply more information to know for sure (ie.e where are 192.168.15.1 and 192.168.3.4 with respect to your 192.168.10.0 network and what path are packets supposed to take to get to/from those other sub-nets?)

---

### Post by csbonito on 2012-12-18
> **Doug S said:**
> What you have described and detailed is how I would expect your system to work.
You can not ping 192.168.15.1 because it is not in your LAN, which is only 192.168.10.0-192.168.10.255. You might need a netmask that includes a larger address space (maybe 255.255.0.0) or add some specific routing (as chadk5utc mentioned). You would have to supply more information to know for sure (ie.e where are 192.168.15.1 and 192.168.3.4 with respect to your 192.168.10.0 network and what path are packets supposed to take to get to/from those other sub-nets?)

netmask 255.255.0.0 worked

Thx alot!

---

