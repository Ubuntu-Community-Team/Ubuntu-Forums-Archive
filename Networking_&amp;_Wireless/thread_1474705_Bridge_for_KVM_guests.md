---
title: "Bridge for KVM guests"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by fireartist on 2010-05-06
My KVM host has a static IP, and I'd like to run 2 (eventually more) virtual guests, each with their own static IP.

My understanding is that I need to create a bridge interface, then create an alias to it, for each guest.

This is the /etc/network/interfaces I've tried most recently.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 1.1.1.100
    netmask 255.255.255.0
    network 1.1.1.0
    broadcast 1.1.1.255
    gateway 1.1.1.1
    dns-nameservers 1.1.2.1
    dns-search subnet.domain.com

auto br0
iface br0 inet manual
    bridge_ports eth0

iface br0:1 inet static
    address 1.1.1.2
    netmask 255.255.255.0
    gateway 1.1.1.1

iface br0:2 inet static
    address 1.1.1.3
    netmask 255.255.255.0
    gateway 1.1.1.1

```I can restart the network service, and there's no error messages - however I lose network connectivity - meaning I can no longer ssh into the host box.

ifconfig lists eth0 and br0, but not br0:1 or br0:2.

Any pointers on how to get this working (preferably using /etc/network/interfaces)?

---

### Post by Burnout on 2010-06-23
I have a similar problem.

I installed ubuntu lucid server and kvm packages. This creates a virbr0 interface which gives my vm's with natted ip's.

But, what I want to do is create a vm with a public IP address. How can this be achived please?


Kind regards,

B.

---

