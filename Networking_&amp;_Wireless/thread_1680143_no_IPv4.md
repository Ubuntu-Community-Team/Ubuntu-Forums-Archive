---
title: "no IPv4"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by Ofloo on 2011-02-02
For a while now when I get open my laptop lid and return from pause mode, the dhcp doesn't assign an IPv4 address to my wlan0 interface, .. 

It does however assign an IPv6, when booting it does assign an IPv4 and IPv6, but when I close the lid and open it again only an IPv6 is assigned. When putting the laptop in offline mode with the disable wifi button and turn it back on then also it gets both IPv4 and IPv6 however when closing the lid (screen) and opening it again it doesn't do that.

An other thing I often, notice is, .. but this is separate from this issue I suppose, is that after while for no good reason networking is disabled, since i don't use gnome-panel this is a bit annoying because then i have to open it check it ... but this doesn't always work, opening gnome-panel I mean, .. I see the screen jump but there is nothing visible, so my next question is how to enable networking from console or something, without opening gnome-panel, because when I open it it is not visible anyways.

---

### Post by mips on 2011-02-02
Have you tried disabling IPv6?

---

### Post by xoomer.ap on 2011-02-02
> **Ofloo said:**
> For a while now when I get open my laptop lid and return from pause mode, the dhcp doesn't assign an IPv4 address to my wlan0 interface, .. 

It does however assign an IPv6, when booting it does assign an IPv4 and IPv6, but when I close the lid and open it again only an IPv6 is assigned. When putting the laptop in offline mode with the disable wifi button and turn it back on then also it gets both IPv4 and IPv6 however when closing the lid (screen) and opening it again it doesn't do that.

An other thing I often, notice is, .. but this is separate from this issue I suppose, is that after while for no good reason networking is disabled, since i don't use gnome-panel this is a bit annoying because then i have to open it check it ... but this doesn't always work, opening gnome-panel I mean, .. I see the screen jump but there is nothing visible, so my next question is how to enable networking from console or something, without opening gnome-panel, because when I open it it is not visible anyways.

Hi!
1st:
Try to disable IPv6. I am not sure that way fix your problem, but if you don't using ipv6, that will be good idea anyway.

Just add under sudo to /etc/sysctl.conf these lines:
```
#
#Disable ipv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
```

2nd:
In my case, turning off radio by functional key on notebook same with executing command
```
sudo iwconfig eth1 txpower off
```
to enable radio:
```
sudo iwconfig eth1 txpower on
```
And, by the way, try to read *man iwconfig* and *man ifconfig*. :)

---

