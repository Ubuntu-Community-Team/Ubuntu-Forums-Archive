---
title: "no IP address"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by doperative on 2011-04-08
They've done something to the local network and Ubuntu will no longer pick up an IP address, it does work in Windows, any solutions please ?

Windows IP Configuration
Host Name . . . . . . . . . . . . : xxxxxxxx
Primary Dns Suffix  . . . . . . . : 
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix  . : 
Description . . . . . . . . . . . : Broadcom
Physical Address. . . . . . . . . : xx-xx-xx-xx-xx-xx
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.xxx.xxx
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.xxx.xxx
DHCP Server . . . . . . . . . . . : 192.168.xxx.xxx
DNS Servers . . . . . . . . . . . : xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx
Lease Obtained. . . . . . . . . . : Friday, April 08, 2011 6:38:06 AM
Lease Expires . . . . . . . . . . : Saturday, April 09, 2012 5:38:06 AM

---

### Post by dineshs on 2011-04-08
please run ```
sudo dhclient
``` and check using ```
ifconfig -a
```

---

### Post by doperative on 2011-04-11
Hey it works ..

ran sudo dhclient and it picked up an IP address .. thanks for the response dineshs ...

> **dineshs said:**
> please run ```
sudo dhclient
``` and check using ```
ifconfig -a
```
Nothing I just see localhost and nothing else, it only happend on one particular network, this might help ..

[http://pastebin.com/7V1LBuYT](http://pastebin.com/7V1LBuYT)

---

