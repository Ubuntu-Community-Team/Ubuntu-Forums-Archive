---
title: "static ip on home network only?"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Naegling23 on 2009-03-14
I use unison to sync files from my desktop to my laptop, this requires that I have a static IP set up.  However, I frequently take my laptop around and connect to other networks.  Is there a way to set a static IP for my home network, and dynamic for all other networks?

---

### Post by puppywhacker on 2009-03-14
you can create an alias eth0:1 which has a static address in addition to your normal interface eth0 with a dhcp address.

you have to define the interfaces in a file, which would then disable the network manager

/etc/network/interfaces
```
auto lo eth0 eth0:1
iface eth0 inet dhcp

iface eth0:1 inet static
        address 192.168.1.9
        netmask 255.255.255.0

```

---

### Post by netztier on 2009-03-14
> **Naegling23 said:**
> I use unison to sync files from my desktop to my laptop, this requires that I have a static IP set up.  However, I frequently take my laptop around and connect to other networks.  Is there a way to set a static IP for my home network, and dynamic for all other networks?

Create a new "wired" profile in NetworkManager, with a static IP address setting (right click on NM's applet, "edit connections", "wired" tab, then "add..." etc.) and give it a meaningful name. So when you're at home, you can just select it from NetworkManager's menu.

regards

Marc

---

