---
title: "Yet another NetworkManager issue: interfaces weirdness"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by rosslaird on 2006-06-17
I've searched and searched the forums without results. So I'm asking:

The nm-applet for NetworkManager shows up on my panel but does not show the network. When I follow the instructions to remove everything except the basics from my interfaces files (then restart networking) I lose all network connectivity and nm-applet still does not work. So the thing that seems to be fixing it for everyone else seems to be making it worse for me.
Here's my current interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

iface eth0 inet dhcp

iface eth1 inet dhcp
#wireless
wireless-mode managed
wireless-essid any
wireless-ap any
auto eth1


```

Help would be good...

Ross

---

