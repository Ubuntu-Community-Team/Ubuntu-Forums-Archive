---
title: "[SOLVED] Routing problem with fixed IP - 8."
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by wamorita on 2009-01-01
I have a problem with the network configuration GUI with respect to routing.
I managed to get the GUI to define a network setup with a fixed IP address (manual).  Getting there was very non-intuitive.
The problem comes with the way the routing is setup by the network configuration editor.  There seems to be no default route.

What I get is this:
[FONT="Courier New"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
[/FONT]
To get my web browser or even the software updater to access the internet, I must do:

[FONT="Courier New"]route add default gw 192.168.1.1[/FONT]

This points to my router.  

_There does not seem to be a way to set a default gateway from this new network configuration editor_!!!!

If anyone knows how to resolve this it would be much appreciated.

---

