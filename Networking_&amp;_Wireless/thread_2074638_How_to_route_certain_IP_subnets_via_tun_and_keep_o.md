---
title: "How to route certain IP subnets via tun and keep other route via wlan?"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by stando007 on 2012-10-22
Hi,

I use vpnc to connect to my company's vpn. But vpnc's script modifies my routing table and after connecting, all my traffic goes via tun0 interface - and this is not good as it is much slower + some services on our vpn's network are blocked.

I would need to let only certain subnet to be routed via tun0 and the rest via my wlan0/default gateway.

This is my default routing table withou vpn connected:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.106   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```


And this is after connectiong to vpn (just for privacy, I marked some parts of IP with xx):
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.xx.xx.0     0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
213.xx.xx.xx    192.168.1.106   255.255.255.255 UGH   0      0        0 wlan0
```

So, how would I correct routing table to route 213.0.0.0 + 172.0.0.0 via tun0 and let other IPs route via wlan0 ? I am not good in this routing stuff, so I would appreciate some help here :)
Thanks!

---

### Post by The Cog on 2012-10-22
Something like these commands (after the VPN is brought up) should do the trick:
```
sudo route del default
sudo route add default gw 192.168.1.106
sudo route add -net 213.0.0.0 netmask 255.0.0.0 tun0
sudo route add -net 172.0.0.0 netmask 255.0.0.0 tun0
```
I would probably put them in a little script, and maybe even make a launcher for them if I needed to do it frequently.

---

### Post by stando007 on 2012-10-26
Thanks much! That simply works for me.

---

