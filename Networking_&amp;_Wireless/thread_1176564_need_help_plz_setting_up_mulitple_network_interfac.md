---
title: "need help plz setting up mulitple network interfaces"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by jeff00z28 on 2009-06-02
The server has multiple network cards. One goes to the network, the other is hooked up to a wasabi storage server with a crossover cable.

I cannot get this to work. This is my config file

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 10.1.30.253
        netmask 255.255.255.0
        network 10.1.30.0
        broadcast 10.1.30.255
        gateway 10.1.30.1

auto eth1
iface eth1 inet static
        address 10.10.11.253
        netmask 255.255.255.252
        network 10.10.11.252

---

### Post by jeff00z28 on 2009-06-02
nevermind another tech installed a bad crossover cable. thank anyway

---

