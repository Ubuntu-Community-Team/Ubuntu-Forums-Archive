---
title: "How to enable multicast forwarding?"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by cconroy on 2009-11-12
I'm running Jaunty 9.04 on x86_64, and I'm trying to enable multicast forwarding on my desktop. Basically, my use case is that I want to take an incoming unicast stream and reroute it out as a multicast stream on the network. I currently have a similar unicast reroute working with iptables.

The problem is that I cannot get multicast forwarding enabled. It defaults to 0 and is readonly, so I cannot just change it. Running a chmod as root also fails.

```
cat /proc/sys/net/ipv4/conf/all/mc_forwarding
0
ls -l /proc/sys/net/ipv4/conf/all/mc_forwarding 
-r--r--r-- 1 root root 0 2009-11-12 18:39 /proc/sys/net/ipv4/conf/all/mc_forwarding
```


I've tried editing /etc/sysctl.conf to include
```
net.ipv4.conf.all.mc_forwarding=1
```

However, there is no change to the value of mc_forwarding after I reboot.

---

