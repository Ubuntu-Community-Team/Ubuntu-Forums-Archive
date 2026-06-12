---
title: "Access_to_WinXP_VPN_server_from_Linux"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by demontager on 2009-10-05
Hi, I'm triyng to connect to WinXP_VPN_server, but can't do that, maybe because my client is beside NAT. My network configuration as shown on screen:
[http://s49.radikal.ru/i126/0910/94/e36db0af4190.jpg](http://s49.radikal.ru/i126/0910/94/e36db0af4190.jpg)

And VPN_connection on WinXP as here:
[http://s44.radikal.ru/i106/0910/2f/9a6b1c9a61fd.jpg](http://s44.radikal.ru/i106/0910/2f/9a6b1c9a61fd.jpg)
Routes on Linux:
```

dem@dem-laptop:~$ sudo route
[sudo] password for dem:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.20    0.0.0.0         UG    0      0        0 wlan0

```

---

