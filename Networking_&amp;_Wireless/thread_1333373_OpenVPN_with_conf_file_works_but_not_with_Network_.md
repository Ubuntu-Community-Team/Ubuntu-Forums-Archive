---
title: "OpenVPN with conf file works but not with Network Manager"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by hiasl on 2009-11-21
Hi,

my setup:
Server (U9.10) with OpenVPN (bridged) - works like a charm
Client (U9.10) with OpenVPN, trying to connect to the server:

1st try via console: "openvpn client.conf" -> works, all routes are set automatically, but DNS Server must be added manually to resolv.conf (although I push it from the server). After that the VPN works perfectly, external Internet connection continues to work.

2nd try via Network Manager: exact same configuration, just via the GUI: VPN connection is established, client gets an IP, some routes are added, DNS Server is added to resolv.conf automatically. Result: internet is working, but not the connection to VPN LAN. DNS is slow because the first DNS Server is from the VPN lan, but can not be reached. it's frustrating. After some time (1-5 minutes) the VPN connection fails.

What I found out is that the routes which are set in the two cases are different:
First one, from console open, working:
```
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
192.168.139.0   192.168.139.53  255.255.255.0   UG    0      0        0 tap0
192.168.139.0   0.0.0.0         255.255.255.0   U     0      0        0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

Second One, from Network Manager, not working:
```
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
78.142.159.250  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.139.0   0.0.0.0         255.255.255.0   U     0      0        0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

So next I manually adjusted the routes. Without any success. Although the routes are idential now, the connection is still broken.

I also checked /var/log/daemon.log, where Network Manager writes to. The only think I found was:
```
Nov 21 17:21:28 hiasl-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

```

However, during the Network Manager VPN connection is up, the tap0 interface exists, so this must result from something else.

Finally I really have the impression, that there is a bug somewhere here.

Does anybody else have made similar positive or negative experiences?

Thanks,
Matthias

---

### Post by Zyprexa on 2009-11-21
Hi

I am sorry that i don't have the experience to be able to help you with your problem, but maybe you could be able to to shed some light on my openvpn problem, in [this thread]("http://ubuntuforums.org/showthread.php?t=1333450")? As you also are running openvpn in bridged mode :)

---

