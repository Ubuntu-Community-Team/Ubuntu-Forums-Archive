---
title: "Wierd wireless problem"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by apauloisdead on 2009-03-24
This only seems to happen at my house... 


When i connect to my network, it's always successful, but sometimes firefox and such won't connect to anything. When i check connection information, i notice my IP address and such are really weird.

```
IP Address: 192.168.15.4
Broadcast Address: 192.168.15.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.15.1
Primary DNS: 192.168.15.1
```

Now i'm no networking pro, but i know that my IP address should be something along the lines of 192.168.1.x, and when it works that's what it is.


I checked my router log and saw this:

```
[Admin login] from source 192.168.1.3, Monday, Mar 23,2009 12:19:58
[DOS attack: UDP Port Scan] attack packets in last 20 sec from ip [192.168.16.1], Monday, Mar 23,2009 12:12:02
[DOS attack: UDP Port Scan] attack packets in last 20 sec from ip [192.168.16.1], Monday, Mar 23,2009 10:58:58
[DHCP IP: (192.168.1.3)] to MAC address 00:18:F3:94:94:60, Monday, Mar 23,2009 10:55:06
```

That was right after one of the times it didn't work.

My windows laptop never has this problem. Any suggestions?

---

