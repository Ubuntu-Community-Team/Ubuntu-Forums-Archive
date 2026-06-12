---
title: "Routing with virtual interfaces"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by sauen on 2011-04-26
I'm trying to set up my WD TV live with my computer.

I have the WDTV and computer connected to ethernet switch which in turn is connected to the cable modem. If I do nothing both devices get a different real IP-address each. And if I try to send something it goes thru the internet.

I tried to add a virtual device to /etc/network/interfaces like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

but then I can't connect to the internet og my computer, but WDTV connection works.

How can I get the computer (192.168.1.1) and WDTV (192.168.1.2) talking thru the switch and everything else thru the modem?

---

