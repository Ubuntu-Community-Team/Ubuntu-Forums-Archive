---
title: "crossover"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by coolmadmax on 2009-04-05
I try to connect my laptop(fedora 10) directly to system(ubuntu 8.04) with crossover network cable.I sign manually ip addresses for network cards and getaway.I still could not establish connection that they can see each other.when i try to connect to server ( ip address of one of them i got massage that could not connect to server). How to make to work LAN ?

---

### Post by Sylslay on 2009-04-05
Meaby I am lame, but did you try set LAN in terminlal
ifconfig eth0 up on both machines.
see configuration file for /etc/networks

for some seting or google for something like this
auto eth0
iface eth0 inet dhcp

---

### Post by albinootje on 2009-04-05
> **coolmadmax said:**
> I try to connect my laptop(fedora 10) directly to system(ubuntu 8.04) with crossover network cable.I sign manually ip addresses for network cards and getaway.I still could not establish connection that they can see each other.when i try to connect to server ( ip address of one of them i got massage that could not connect to server). How to make to work LAN ?

So you have two machines which only talks to each other, right ?
Or does the desktop system have a second NIC which gets internet via that second NIC ?
If you only use a crosslink cable, and nothing else, you would not set a gateway.
Just give both an ip address in the same network range, and try to ping the other (provided that firewall software allows ping answers on ping requests).

---

### Post by superprash2003 on 2009-04-05
what are the ips you have set? try pinging the ips from the terminal

---

