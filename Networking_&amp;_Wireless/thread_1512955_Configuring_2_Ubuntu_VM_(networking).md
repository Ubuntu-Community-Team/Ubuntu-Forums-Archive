---
title: "Configuring 2 Ubuntu VM (networking)"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by _alee_ on 2010-06-18
Hi, 

I have latest ubuntu and I have made 3 vm's for them.

VM 1: with 2 NIC cards, one is NAT connected directly through my host machine to the internet with ip address 192.168.190.142. Second NIC card is "host only" with ip address 192.168.0.10

VM 2: with 1 NIC card, "host only" and ip address 192.168.0.100

I want VM 2 to connect to the internet but through VM 1. for this I used following configuration in ```
/etc/network/interfaces
``` but it is not working

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
    address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.10

```

I have given my VM 2 the gateway of VM 1 but it is not going through. Am i doing something wrong. Could someone please help me?

P.S:
both machines are pinging each other properly.

---

### Post by _alee_ on 2010-06-18
anyone,Please help. its really urgent.

---

