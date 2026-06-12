---
title: "Jaunty Cisco VPN"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by shaamone on 2009-05-05
I'm using the built-in vpn client in Jaunty and can connect successfully to my Cisco 1801 at home. The 'route' command shows the following routing table. However, I cannot ping or communicate with any addresses on the remote network.

This config works perfectly using the Cisco VPN client in Windows, so I'm confident my router config is good. Any ideas?

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
78-xx-xx-42.zon 172.16.1.1      255.255.255.255 UGH   0      0        0 wlan0
10.1.12.0       *               255.255.255.0   U     0      0        0 tun0
10.1.8.0        *               255.255.255.0   U     0      0        0 tun0
10.1.10.0       *               255.255.255.0   U     0      0        0 tun0
10.1.11.0       *               255.255.255.0   U     0      0        0 tun0
172.16.1.0      *               255.255.255.0   U     2      0        0 wlan0
default         172.16.1.1      0.0.0.0         UG    0      0        0 wlan0

```

---

