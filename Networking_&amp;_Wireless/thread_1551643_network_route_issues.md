---
title: "network route issues"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by lysalf on 2010-08-12
Hi all. 

Trying to get some understanding of the route tables.

My case is the following.

I have a box with 2 NICs (ath0 & eth0).

I connect to a wireless router(and the internet) via dhcp on ath0. address assigned an 192.168.1.X address.

From my eth0 (wired interface) i like to connect directly to a NAS box I have that only this linux box should be able to use.

How would my network setup be, and should i use "route add -host" or something like that.

---

### Post by Iowan on 2010-08-12
If eth0 and the NAS box have addresses in the same subnet (outside the 192.168.1.X subnet), they *should* be able to see (ping) each other. This also assumes proper cabling - gigabit NIC's might auto-configure, but the 10/100 NIC's I use require a crossover cable to go machine-machine.

---

### Post by lysalf on 2010-08-13
Hi the cabling is correct as it is a gigabit NIC. But what gateway should i use to define eth0 ? eg if subnet 192.168.2.X is used ?

If i use same gateway for eth0 and ath0 the eth0 has a higher priority and all traffic will be routed to eth0 NIC

What i am looking for i a ruleset to route all traffic to ath0 NIC except when a certain ip address.

---

### Post by YesWeCan on 2010-08-13
You don't need to define eth0 with a gateway. If I understand your correctly, you should set eth0 with a static address, such as 192.168.2.1 (not the same as your NAS, obviously) in /etc/network/interfaces. You already have ath0 defined as dhcp.
Then sudo /etc/networking restart

route -n
You should now have a route to 192.168.2.0/24 dev eth0 and a route to ath0 and a default gateway via ath0.

---

### Post by Iowan on 2010-08-13
The gateway is used for "all other" traffic that doesn't already have a route specified. As such, there should be only one. You can post the results of **route -n**.

---

### Post by lysalf on 2010-09-10
Thanks for the info, the "there can be only one" gateway solved my headaches.

---

