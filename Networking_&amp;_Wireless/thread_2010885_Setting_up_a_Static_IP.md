---
title: "Setting up a Static IP"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by Auroraah on 2012-06-26
Hi everyone,

I need to set up a static IP for my Ubuntu, so I read what is needed to do with the "eth0" in /etc/network/interfaces. I go to that file and all it contains is:

auto lo
iface lo inet loopback

How do I change my Ubuntu to use "eth0"?

I have static IP set up on all my other Windows PC's and I need it for this one too. If it matters I'm using Ubuntu 12.04.

---

### Post by Cheesemill on 2012-06-26
If you are using the normal desktop version of Ubuntu then don't edit /etc/network/interfaces.

Instead you should go to Settings > Network > Options > IPv4 Settings and make your changes there.

---

### Post by asmoore82 on 2012-06-26
+1 for going through the standard NetworkManager GUI - with admin rights, you can overwrite the standard "auto" profile to be static instead.

Setting this in /etc will not bring your interface up and down for you when Ethernet is hot-plugged. But just for completeness, it looks something like this:
```
#/etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.11
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

---

