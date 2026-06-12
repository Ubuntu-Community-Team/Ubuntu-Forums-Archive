---
title: "routing questions"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by keimasi on 2011-02-13
**hi to all of friends**


I wanna use a pc with linux os as a router.I dont hv 2 eth, i only hv 1. does is work as a router if I assign 2 difference if? Or I have to have 2 eth?

pls guide me if it is possible.
tnx:KS

---

### Post by dmizer on 2011-02-14
You'll probably have to do it in /etc/network/interfaces which means you'll have to uninstall network-manager.

You can add a second child interface in /etc/network/interfaces like so:
```
auto lo
iface lo inet loopback

## Physical NIC ##
auto eth0
iface eth0 inet dhcp

## Child interface ##
auto eth0[COLOR="Red"]:1[/COLOR]
iface eth0[COLOR="Red"]:1[/COLOR] inet dhcp
```
You can add up to 255 child interfaces.

eth0:0
eth0:1
eth0:2
eth0:3
etc.

---

### Post by keimasi on 2011-02-14
thanks for ur reply. so I hv 2 use 2 eth0 for change linux to a router. isnt it?
:KS

---

### Post by dmizer on 2011-02-14
> **keimasi said:**
> thanks for ur reply. so I hv 2 use 2 eth0 for change linux to a router. isnt it?
:KS

No, eth0 was an example. You can use wlan0, wlan0:0, wlan0:1 and so on if you like. Or, if your device is eth3, you can use eth3, eth3:0, eth3:1 and so on.

---

### Post by keimasi on 2011-02-15
ok
tnx:KS

---

