---
title: "Multiple Connections, Routing Failure"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by daxumaming on 2010-12-08
The company I'm working for has 2 network connections. The wired connection is used for local/LAN servers, while the wireless connection's for Internet access. Both are configured for static IP, with the router physically relocated from the wired to wireless.

Here's my current setup
eth0 IP: 192.168.15.222 Gateway: 192.168.13.1 (although this one is physically disconnected) Netmask: 255.255.252.0
wlan0 IP: 192.168.13.52 Gateway: 192.168.13.1 Netmask: 255.255.252.0

route -n
Kernel IP routing table
Destination   Gateway       Genmask        Flags Metric Ref Use Iface
0.0.0.0       192.168.13.1  255.255.252.0  UG    0      0    0 wlan0
192.168.12.0  0.0.0.0       255.255.252.0  U     1      0    0 eth0
192.168.12.0  0.0.0.0       255.255.252.0  U     2      0    0 wlan0
169.254.0.0   0.0.0.0       255.255.0.0    U     1000   0    0 eth0
0.0.0.0       192.168.13.1  0.0.0.0        UG    0      0    0 wlan0

Both connections are managed by Network Manager. The Wired Connection has ***Use this connection only for resources on its network*** enabled. While the Wireless connection has nothing under routes.

I also executed ***sudo route add default gw 192.168.13.1 netmask 255.255.252.0 wlan0*** to make sure that all requests are routed through the wireless connection.

My problem is, only the Wired Connection has access, while Wireless keeps on disconnecting. After I disconnected the Wired, the Wireless would connect without problems. But after reconnecting, the Wireless would lose connectivity after a few seconds to a few minutes. Sometimes, ping would just freeze. It won't stop or fail... just freeze until I disconnect the Wired connection.

Any help would be appreciated. Thank you

---

### Post by daxumaming on 2010-12-08
changing eth0's Netmask to 255.255.255.0 and Gateway to 0.0.0.0 (since it's not there to begin with) may have fixed my problem. Will report back in a day or two after I've verified that it worked.

UPDATE
confirming the above workaround, didn't have any DC and both my connection's working flawlessly.

---

