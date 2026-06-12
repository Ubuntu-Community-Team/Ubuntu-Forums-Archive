---
title: "How to configure IPv6?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by smartbone on 2009-04-30
I have just installed Ubuntu 9.04, everything goes fine except for the IPv6 configuration.
I used to configure IPv6 successfully in my fedora release and it's quite straight forward: 

Code:
  ifconfig eth0 inet6 add 2001:cc0:2044:0::73
  route -A inet6 add ::/0 gw 2001:cc0:2044:0::1

But in ubuntu these commands do not work. 
I am very new to linux and know little thing about network configuration, could someone help me out, thank you very much!

---

