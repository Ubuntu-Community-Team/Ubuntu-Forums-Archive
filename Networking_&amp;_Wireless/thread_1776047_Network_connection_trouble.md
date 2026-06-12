---
title: "Network connection trouble"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by Guruprasad on 2011-06-05
I have two networks, one for internet with DHCP and other for LAN with static IP.

Ubuntu 10.04 created two network connections automatically "Wired Connection 1" which I set as DHCP and "Wired Connection 2" which I configured with static IP. 

The problem is that when I start my computer some times "Wired Connection 2" is assign to both the network or sometimes "wired connection 1" gets assigns to both network. Some times Wired connection 2 goes missing.

I remember couple of years back I use tp edit "/etc/network/interfaces" to set network. Presently my "/etc/network/interfaces" have only following lines

> auto lo
iface lo inet loopback

How do I rectify this problem?

---

