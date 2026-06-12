---
title: "after wireless connected, connection unstable"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by istvank on 2009-11-01
A have a weird problem with the wireless network connection.
After I setup the wireless, it gets the IP address from DHCP and from that moment the network starts to be unstable on both network interfaces(eth0 and wlan0). By unstable I mean, there are periods of time out(8 - 50 sec), the ping gets reply between 10 - 15000 ms(normally is <1ms). This happens even if I disable eth0.
The router is ok. I have other computers connected to it, working just fine.
Any ideas?

I forgot. I'm using Ubuntu 9.04 or maybe 9.10, if apt-get update upgrades the distribution.

---

### Post by aimaaditya on 2009-11-01
hi,
even i having this trouble ever since my coll decided to go with MAC filtering with wireless access points...i am able to connect with dual booted win7 on the same system as well as with karmic on wep enabled access points..but not on MAC filtered ones...i am able to connect using Win 7 though.....

so, everything works except connection to MAC filtered access points gets dropped...

---

### Post by istvank on 2009-11-02
It look like installing wicd solves the problem:
sudo apt-get install wicd

---

