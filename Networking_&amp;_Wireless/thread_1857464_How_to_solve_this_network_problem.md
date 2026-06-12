---
title: "How to solve this network problem?"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by newhere_m on 2011-10-10
I used these command to setup network connection in my ubuntu 10.04 LTS:
```

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf

```Then I use the commands "sudo pon dsl-provider" to connect to net. Nowadays this command is not giving desired result. The result of plog shows (only relevant parts given):
```

Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
pppd 2.4.5 started by root, uid 0
error sending pppoe packet: Network is down
error receiving pppoe packet: Network is down

```At this point if I use the command "sudo dhclient eth0" then I am able to connect to the net. What is going wrong? Why do I get "Network is down" report with "pon" command?

I have blindly used the command "sudo dhclient eth0" as advised by someone to solve another problem. Can anybody please explain its action?

---

### Post by redmk2 on 2011-10-10
> **newhere_m said:**
> I used these command to setup network connection in my ubuntu 10.04 LTS:
```

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf

```Then I use the commands "sudo pon dsl-provider" to connect to net. Nowadays this command is not giving desired result. The result of plog shows (only relevant parts given):
```

Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
pppd 2.4.5 started by root, uid 0
error sending pppoe packet: Network is down
error receiving pppoe packet: Network is down

```At this point if I use the command "sudo dhclient eth0" then I am able to connect to the net. What is going wrong? Why do I get "Network is down" report with "pon" command?

I have blindly used the command "sudo dhclient eth0" as advised by someone to solve another problem. Can anybody please explain its action?

You are requesting (and it appears receiving) an IP address via a DHCP server that is residing on your network.  On a small LAN,  DHCP services are usually supplied by your router.

---

### Post by dineshs on 2011-10-10
Can you post the results of ```
cat /etc/network/interfaces
```and ```
sudo dhclient eth0
```

---

### Post by newhere_m on 2011-10-10
Thanks for attention. The results are as follows: 
```

$cat /etc/network/interfaces

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```
```

$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/yy:yy:yy:yy:yy:yy
Sending on   LPF/eth0/yy:yy:yy:yy:yy:yy
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.9 on eth0 to 255.255.255.255 port xx
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth0 to 255.255.255.255 port xx interval 7
DHCPOFFER of 192.168.1.9 from 192.168.1.1
DHCPREQUEST of 192.168.1.9 on eth0 to 255.255.255.255 port xx
DHCPACK of 192.168.1.9 from 192.168.1.1
bound to 192.168.1.9 -- renewal in 38264 seconds.

```
I have replaced some digits by yy and xx. Hope these won't cause problem.

---

### Post by dineshs on 2011-10-11
Please run```
sudo gedit /etc/network/interfaces
```Let the file contain only the first two lines ie```
auto lo
iface lo inet loopback
```Restart PC and see if sudo pon dsl-provider connects.
You may also try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9").

---

