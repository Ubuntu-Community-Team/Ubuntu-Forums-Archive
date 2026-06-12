---
title: "VPN - no access to remote computers"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by mqqla on 2010-11-14
Hi all,

I've got strange problem with my VPN connection I configured on my server and client.
I cannot access other remote machines than my VPN endpoint.

I configured pptpd on Ubuntu server (10.10) as follows:
localip 192.168.15.30
remoteip 192.168.15.210-240

192.168.15.30 is my remote server which serves the VPN for my 'office' network (of course it has public IP also :)
192.168.15.20 is other server in the network end neither ping nor telnet to it's open port works :(

My client computer (Ubuntu 10.10) gets the IP 192.168.15.210 interface ppp0.
Identical interface shows on server side - 192.168.15.210 ppp0

On client side netstat -rn shows:

```
192.168.15.1    0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.15.30   0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.15.0    192.168.15.1    255.255.255.0   UG        0 0          0 ppp0

```

I added one route entry on client's advanced VPN config:
192.168.15.0,255.255.255.0,192.168.15.1,1
But with and without this entry problem still exists.

My server's netstat -rn is:
```
192.168.15.210  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.15.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG        0 0          0 eth0

```

what's strange for me - inetrface ppp0 (server side) has addres 192.168.15.210 with netmask 255.255.255.255... And there's no 24bit mask - should it have to connect to other machines?

I checked the situation on windows client, which regularly connects to the other vpn and the problem is the same - it pings 15.30 and has no access to 15.20, 15.10 machines.

any suggestions?

regards
m

---

