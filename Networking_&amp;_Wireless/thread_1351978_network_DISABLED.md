---
title: "network DISABLED"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Spudinski on 2009-12-11
Hey guys,

So I've installed Ubuntu 8.04 on Virtual Box.
I've set the network in V'box to be bridged, the network connection on my host computer shows it's all good, IP is set and all.

My host is winXp and the guest is Ubuntu(8.04).
When I use /etc/init.d/networking restart I get something like:
```
eth0: ERROR while getting interface flags: No such device
```
And then just errors about the addr and netmask not being able to be set(obvious so I won't present that).

Now, I tried to read up on this a little on Google, but I haven't found anything useful.
The weird thing that gets me is, lshw shows me that it picks up the network adapter just fine, but it has something like "*-network DISABLED", so I really don't know about that.

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
```
This is exactly how the network for the V'box is on my host computer, I had to change it from DHCP.

Any help guys?

---

