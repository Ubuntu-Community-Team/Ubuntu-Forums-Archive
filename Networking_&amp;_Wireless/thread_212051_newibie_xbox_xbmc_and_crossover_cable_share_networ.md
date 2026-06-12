---
title: "newibie xbox xbmc and crossover cable share network"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by f76 on 2006-07-09
I was looking to share my static ip internet connection in my pc running ubuntu with my xbox. Its not that i figured anything new - I just want to point out that this alternative works.

follow [NEWBIE HOWTO: Get Firestarter to work the FIRST TIME]("http://www.ubuntuforums.org/showthread.php?t=74925")

and in your network setup in xbmc just set assignment to DHCP and restart.

Thats it.

---

### Post by woedend on 2006-07-09
or skip the DHCP step/daemon alltogether and just use static on the xbox...its a 2 minute process.
In fact, there is even one line you can type to enable sharing that i've saved to a script should you not want firestarter to do it :) here it is broken down with commenting.
```

#load module
modprobe iptable_nat
#replace eth1 with device connected to internet, not xbox
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

### Post by f76 on 2006-07-12
thanks!

---

