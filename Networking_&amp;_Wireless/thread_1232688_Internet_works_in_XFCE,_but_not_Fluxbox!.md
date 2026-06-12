---
title: "Internet works in XFCE, but not Fluxbox!"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by alberto.the.peguin on 2009-08-05
I installed Fluxbox through synaptic and for some reason the internet will not work when I use that window manager at all (both wireless and ethernet). But both work when I use XFCE and I've installed fluxbox on my desktop already with a successful internet connection (I'm trying to on a laptop now). I've tried searching, but this seems to be a strange problem no one else is having. Can anyone even point me in a direction that may help? I've been trying to solve this for a week.

---

### Post by kerry_s on 2009-08-05
you need to put the network manager in fluxbox startup or skip using a network manager & put the settings in to /etc/network/interfaces.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# The primary wireless interface
allow-hotplug wlan0
iface wlan0 inet dhcp
wireless-essid newday


```

---

