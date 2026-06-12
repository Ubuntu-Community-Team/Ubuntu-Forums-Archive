---
title: "Configuring my enthranet controller"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by a12ctic on 2006-06-13
Hey, ive been going at this for a few days, my buddies windows xp partion decided to quit on him. i suggested linux, the installation went fine, but his enthranet controller wont work.

lscpi output:
0000:02:01.1 ethernet controller: realtek semiconductor co. ltd. rtl-8139/81390/8139C+ (rev 10)


/etc/network/interfaces:

iface eth0 inet dhco

auto lo
iface lo inet loopback

iface eth1 inet dhcp

auto eth2
iface th2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0

its not conecting to the router and i cant seem to get it to work, dhcp always seemed automatic to me, what am i missing

---

