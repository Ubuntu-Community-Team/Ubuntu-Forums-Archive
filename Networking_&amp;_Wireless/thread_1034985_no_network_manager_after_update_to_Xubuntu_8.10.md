---
title: "no network manager after update to Xubuntu 8.10"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by miocene on 2009-01-09
I've just updated my Xubuntu up from 8.04 to 8.10

Wierdly, my Belkin 54g card (BCM43xx) which has caused me so many difficulties getting working on linux is working great and I can access the internet no probs.
But in the network icon in the taskbar there is a small ! mark on it and when I click nothing is selectable and it says "device is unmanaged".

Also, in preferences/settings there is no network manager like there was in 8.04.

---

### Post by cmnorton on 2009-01-09
You may have to preserve and then fiddle with your /etc/network/interfaces file -- using sudo -- to make it look more like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by miocene on 2009-01-10
Ok, how do I open this file using sudo?

---

### Post by cmnorton on 2009-01-11
sudo vi /etc/network/interfaces

sudo gkedit /etc/network/interfaces

---

