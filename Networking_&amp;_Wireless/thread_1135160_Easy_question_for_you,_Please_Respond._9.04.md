---
title: "Easy question for you, Please Respond. 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by dragonbeast25 on 2009-04-24
My d-link router WBR-1310 is showing the the windows computer has a icon on the dlink to show it connected, same with my xbox 360, but when i go on ubuntu it dosnt show so basicly the ethernet dsl cord is not connected to my router but it is, but ubuntu OS dosnt show on my router ? Help. Thank you ASAP>

---

### Post by Iowan on 2009-04-24
I don't have a D-Link router, so some of the icon details slipped by me, but...
*IF* the router is the DHCP server, and *if* the machines get IP addresses via DHCP, you might edit /etc/dhcp3/dhclient.conf and include your machine hostname on the line ```
send host-name "<hostname>";
```

---

