---
title: "IP on Multiple LAN Cards"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by neandero on 2013-02-06
my settings inside /etc/network/interfaces are:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 123.123.123.22
netmast 255.255.255.248
gateway 123.123.123.17


only one network will work at a time.
even adding the below line:


route add default gw 123.123.123.17
--OR--
route add default gw 192.168.5.254

What can be done to make both networks work at the same time??

thanks,

---

### Post by jonobr on 2013-02-06
Hello


When you add your default gateway as one or the other then all traffic will go to that device


I guess what you may be looking for is split access
[here]("http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html#AEN258")

---

