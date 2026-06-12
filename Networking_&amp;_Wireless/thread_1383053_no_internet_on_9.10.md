---
title: "no internet on 9.10"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by nathanieldouglas on 2010-01-16
I know there have been a lot of discussions on this - and I have searched and tried many or most - but I think this is new:

I'm getting no internet recognition at all, no pings, nothing - it's a new install of 9.10, which was actually working very well for me for weeks, until today when I decided to get smart and clear my other partitions and work exclusively with Karmic Koala - MUCH TO MY DISMAY!

I'm on a friend's computer for this because I can't even get a wired response or anything.  Oh - it's a Lenovo s10 by the way.

I beseech ye, forum.  Thank you!

---

### Post by scragar on 2010-01-16
Could you please return the output of ```
ifconfig
```

---

### Post by nathanieldouglas on 2010-01-16
Thanks for picking on this - sorry for delay; ifconfig is as follows:

eth0    Link encap: Ethernet  Hwaddr  00:23:5a:d0:4f:7c
          UP BROADCAST MULTI    MTU:1500   Metric:1 
          RX packets:1095  errors:0  dropped:0  overruns:0   frame:0
          TX packets:11   errors0   dropped:0   overruns:0  carrier:0
          collisions:0   txqueuelen:1000
          RX bytes:68682  (68.6KB)   TX bytes:2178  (2.1 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1   Mask:255.0.0.0
          inet6 addr:  ::1/128  Scope:Host
          UP LOOPBACK RUNNING   MTU:16436   Metric:1
          RX packets:0  errors:0  dropped:0  overruns:0  frame:0
          TX packets:0  errors0   dropped:0   overruns:0  carrier:0
          collisions:0   txqueuelen:0
          RX bytes:0  (0.0 B)   TX bytes:0  (0.0 B)


I also know that I'm getting "UNCLAIMED" for the Network Controller when I enter
sudo lshw -C network
but no such error for Ethernet interface under same same command

thanks.

---

