---
title: "Connecting to two Networks at the Same Time (Ubuntu 11.04)"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by despuit on 2011-11-18
I am experiencing a similar problem as the one stated at: [http://ubuntuforums.org/archive/index.php/t-1770115.html](http://ubuntuforums.org/archive/index.php/t-1770115.html)

However I've already routed it so it uses only resources on that network and my internet is still not kicking in on the wireless network (WLAN0).

This is my routing table:

192.168.2.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0
192.254.0.0 0.0.0.0 255.255.255.0 U 1000 0 0 wlan0
0.0.0.0 192.168.2.254 0.0.0.0 UG 0 0 0 eth0

On my PC it works and this is how I have it configured:

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::608e:d472:86f7:b68b%14
   IPv4 Address. . . . . . . . . . . : 192.168.1.111
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter (6) Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::f109:c88e:4758:eab%12
   IPv4 Address. . . . . . . . . . . : 192.168.2.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.2.254


Same as the way I set Linux now but no results on that side. Any ideas?

----------------------

Not sure how to delete this post but I resolved this, had to reset all the network interfaces and flush them and then reconnect to the networks then I had no problems.

---

### Post by jonobr on 2011-11-18
You Have the option to change the status to solved so people searching can find a solution 

Good you followed up though!

---

