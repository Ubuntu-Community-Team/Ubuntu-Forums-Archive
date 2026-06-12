---
title: "Routing broken after NetworkManager uninstall/reinstall. Please help."
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by far_star on 2009-01-21
Strangest thing. On a whim I did an iptables -F and things are fine. How iptables got configured to cripple my connection is beyond me. I just want to disable it upon reboots. Can anyone help with this simple one ?


My GW is 192.168.1.254 

The output of route is
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0


I cannot ping beyond the GW and DNS is obviously broken for the same reason. Can anyone help ?

---

