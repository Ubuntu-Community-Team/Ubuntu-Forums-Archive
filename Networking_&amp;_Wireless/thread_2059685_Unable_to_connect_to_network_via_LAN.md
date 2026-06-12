---
title: "Unable to connect to network via LAN"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by eshkaml on 2012-09-18
Hi I am unable to connect to a network via LAN. I m firing these two commands.
sudo ifconfig eth0 <IP> netmask 255.255.255.0
sudo route add default gw <GWay> eth0


Every time I am getting response for some second then it is showing NETWORK IS UNREACHABLE.

But I have tried from other Ubuntu machine. It is working fine.

---

### Post by Iowan on 2012-09-18
You may be butting heads with Network Manager...
What are results of **ifconfig -a** and **route -n**?

---

