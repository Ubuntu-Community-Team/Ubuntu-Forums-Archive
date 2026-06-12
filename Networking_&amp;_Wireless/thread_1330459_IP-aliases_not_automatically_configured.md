---
title: "IP-aliases not automatically configured"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by alphager on 2009-11-18
I am experiencing a strange phenomenon regarding multiple IP-adresses on one NIC on an Ubuntu server.

My /etc/network/interfaces looks like this (XX.XX.XX being identical in each occurrence):
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address XX.XX.XX.46
        netmask 255.255.255.0
        network XX.XX.XX.0
        broadcast XX.XX.XX.255
        gateway XX.XX.XX.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers YY.YY.YY.YY ZZ.ZZ.ZZ.ZZ

auto eth0:1
iface eth0:1 inet static
        address XX.XX.XX.48
        netmask 255.255.255.0
        network XX.XX.XX.0
        broadcast XX.XX.XX.255
#        gateway XX.XX.XX.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers YY.YY.YY.YY ZZ.ZZ.ZZ.ZZ

auto eth0:2
iface eth0:2 inet static
        address XX.XX.XX.47
        netmask 255.255.255.0
        network XX.XX.XX.0
        broadcast XX.XX.XX.255
#        gateway XX.XX.XX.1
        # dns-* options are implemented by the resolvconf package, if installed
       dns-nameservers YY.YY.YY.YY ZZ.ZZ.ZZ.ZZ

auto eth0:3
iface eth0:3 inet static
        address XX.XX.XX.49
        netmask 255.255.255.0
        network XX.XX.XX.0
        broadcast XX.XX.XX.255
       dns-nameservers YY.YY.YY.YY ZZ.ZZ.ZZ.ZZ


```Using Kernel 2.6.24.2, this works.
Booting Kernel 2.6.28, this setup only brings up eth0; eth0:1, eth0:2 and eth0:3 are not brought up. Manually bringing them up by using "sudo ifup eth0:1" works fine.

What do i have to do so that eth0:1 is brought up automatically? I have an up-to-date Jaunty-system, which began it's life as a hardy.

---

### Post by Iowan on 2009-11-18
> **alphager said:**
> 
My /etc/network/interfaces looks like this (XX.XX.XX being identical in each occurrence)You're trying to put all four interfaces in the same subnet?

---

### Post by alphager on 2009-11-19
> **Iowan said:**
> You're trying to put all four interfaces in the same subnet?
Yes. It's an internet-facing server and i run 3 SSL-enabled sites on it.

---

