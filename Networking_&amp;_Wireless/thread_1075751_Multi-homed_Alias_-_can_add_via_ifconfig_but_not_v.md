---
title: "Multi-homed/ Alias - can add via ifconfig but not via ifconfig eth0:0 192.168.5.10???"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by jimwillsher on 2009-02-20
Very confusing! My server has one NIC, IP 192.168.1.50, subnet 255.255.255.0. I wish to add an alias IP in a different subnet. If I enter

ifconfig eth0:2 192.168.5.100 netmask 255.255.255.0 up

it starts ok. But if I instead edit /etc/network/interfaces and add an alias in there I get:

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFADDR: File exists
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Failed to bring up eth0:2.


My /etc/network/interfaces is:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.50
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

auto eth0:2
iface eth0:2 inet static
        address 192.168.5.100
        netmask 255.255.255.0

```

What am I missing please?

2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64 GNU/Linux



Jim

---

