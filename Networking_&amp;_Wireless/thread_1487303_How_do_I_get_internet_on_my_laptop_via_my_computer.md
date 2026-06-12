---
title: "How do I get internet on my laptop via my computer?"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by compiz addict on 2010-05-18
I'm trying to connect my laptop (running Puppy Linux right now, but I might change the distro later). to my desktop (Running Ubuntu 10.04 Lucid Lynx). My desktop is connected via wireless, and I want to connect my laptop to it using my D-Link router and my two internet cords.

---

### Post by sedawk on 2010-05-19
You have two networks, the wireless and the (new) wired
one connecting the two machines (you don't need a router
for that - you can try to connect both machines directly
with a cable. But depending on your hardware it might require
a special cross-over-cable).
You have to choose a network so that your two PCs on the
wired network have their own subnet.
E.g if your wireless is 192.168.1.*/255.255.255.0
you can use 192.168.2.*/255.255.255.0  for the wired network.

There are two ways to get the internet connection.
First you can configure your desktop PC to act as a router,
then all traffic from the wired network that is targeted
towards external IPs will go to the wireless network.
For this you have to enable "IP forwarding".

A more secure solution would be to install a proxy on
the desktop (I recommend privoxy) and your laptop can only
talk to that proxy. The proxy will forward all requests
from the wired network to the wireless network. So you can
browse the internet from the laptop but applications that 
require a direct connection will not work.

---

