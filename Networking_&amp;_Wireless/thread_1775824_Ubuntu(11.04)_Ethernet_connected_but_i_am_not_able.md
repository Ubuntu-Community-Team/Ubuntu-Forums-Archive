---
title: "Ubuntu(11.04) Ethernet connected but i am not able to access the internet...."
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by jhansiyb on 2011-06-05
[RIGHT][/RIGHT]Hi.........
I am using ubuntu (11.04) here, when i connect Bsnl broadband link(wired connection).
Internet is connect automatically But unable to instal, upgrad and access Internet pages ..
Don't know why it happens..........

---

### Post by chili555 on 2011-06-05
Please run in a terminal:```
ifconfig
```If the IP address is 10.43.42.xx, then your computer thinks you want an ad-hoc or computer-to-computer connection. You can check by clicking the Network Manager icon and select Edit Connections. Edit Auto eth0. and select IPv4 settings. The drop-down should be set for Automatic DHCP and not Shared to other computers.

If ifconfig shows that you have a 192.168.x.y address showing you are connected to a router or you have a direct BNSL address with no router, then it is probable that you have no valid DNS nameservers. In that case, please post:```
cat /etc/resolv.conf
route -n
```

---

