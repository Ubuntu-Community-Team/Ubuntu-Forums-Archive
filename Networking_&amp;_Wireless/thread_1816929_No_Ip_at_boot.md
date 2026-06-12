---
title: "No Ip at boot"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by LSum on 2011-08-02
Dear all,

I just reinstalled one of my ubuntu machines with ubuntu server 10.04
to have a gui needid for setting up and maintaining some of the software rounning on this machine  i installed Xorg and gnome-core
and this is working perfectly fine except that since the installation the machine is not getting an IP adress

```
sudo dhclient eth0
```is solving the problem tough
there are more persons working on this machine who don't have root permissions

I've checked the /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

```I hope someone can help me fixing my problem

thanx

---

### Post by chili555 on 2011-08-02
You need to tell *interfaces* how you need to connect; e.g.:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface inet eth0 [COLOR="Red"]dhcp[/COLOR]
```Of course, if it's a server, you may prefer static.

---

