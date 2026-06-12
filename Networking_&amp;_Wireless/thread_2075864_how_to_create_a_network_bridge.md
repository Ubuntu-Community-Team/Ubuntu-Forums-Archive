---
title: "how to create a network bridge?"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by kidd4200 on 2012-10-24
so how do i do it?
id like to make it static via /etc/network/interfaces

id like to bridge my wlan0 and my eth0, then have both of em working on ip 192.168.0.15

my SSID is venom, and NO password or whatever. its open, completely (internet should be free anyways right?)

also, i do have bridge-utils

heres what i got saved currently :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.15
        netmask 255.255.255.0
        gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

