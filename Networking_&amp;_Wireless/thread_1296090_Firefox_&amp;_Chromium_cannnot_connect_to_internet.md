---
title: "Firefox &amp; Chromium cannnot connect to internet"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by figo2476 on 2009-10-20
Hi,

I updated my Dell D610 to Ubuntu 9.10 Today. I know it is beta, but I want to try out new stuff.

Here is some info:
* I can ping google.com
* Firefox & Chromium cannnot connect to internet
* sudo apt-get update, it says "connect to archive.canonical.com (1.0.0.0)".
It stuck there basically.

---

### Post by figo2476 on 2009-10-20
Hi,

I realized that FF & Chromium are able to connect to the internet, when I am back to uni. (I upgraded to Karmic in uni as well)

It is still **not** working at home.


FYI

tracepath google.com
 1:  username.local (10.1.1.3)                              0.212ms pmtu 1500
 1:  no reply
 2:  no reply
 .....


route -n          
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     1      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

---

