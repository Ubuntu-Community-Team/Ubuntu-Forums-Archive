---
title: "Help with promiscuous"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by cooldude786 on 2012-08-25
Hi,

I am using ubuntu 10.04. I have only one interface eth0. I want to use the promiscuous mode. When i run the following command in /etc/network/interface:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.14
  gateway 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  post-up for i in rx tx sg tso ufo gso gro lro; do ethtool -K $IFACE $i off; done

I get an long program as an error when i do networking restart. Please help!!!

Thank you

---

### Post by MG&amp;TL on 2012-08-26
Bearing in mind this is "Absolute beginner talk" you might be better off in "Networking and Wireless" next time.

We can't go on much if you don't give us the error. Can we have that, please?

---

### Post by sffvba[e0rt on 2012-08-26
*Thread moved to **Networking & Wireless**.*


404

---

