---
title: "Cannot change to static ip"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by false_chicken on 2011-02-01
I am running ubuntu server and have set my interfaces file up properly and set a static dns but it keeps connecting with dhcp. When I start the networking I get the following.

administrator@Pineapple-Server:~$ sudo /etc/init.d/networking restart
[sudo] password for administrator: 
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth0.pid with pid 20971
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:11:11:3d:13:d6
Sending on   LPF/eth0/00:11:11:3d:13:d6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:11:11:3d:13:d6
Sending on   LPF/eth0/00:11:11:3d:13:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.17 from 192.168.2.1
DHCPREQUEST of 192.168.2.17 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.17 from 192.168.2.1
bound to 192.168.2.17 -- renewal in 850911745 seconds.
ssh stop/waiting
ssh start/running, process 21101

How can I disable this? Thanks.

---

### Post by matt_symes on 2011-02-01
Hi

There are some suggestions here.

[http://ubuntuforums.org/showthread.php?t=1374799](http://ubuntuforums.org/showthread.php?t=1374799)

Kind regards

---

### Post by false_chicken on 2011-02-01
None of those work unfortunately:(

---

### Post by matt_symes on 2011-02-01
Hi

Can you post the output of

```
cat /etc/network/interfaces
cat /etc/resolv.conf
lsattr /etc/network/interfaces
ps aux | grep dhcp
```

Did you uninstall the dhcp client ? 

Kind regards

---

### Post by false_chicken on 2011-02-01
Ok Now I am confused. I went into interfaces to make sure it was right. I sudo into nano to find i dont have write permissions O_o Any sugestions?

---

### Post by matt_symes on 2011-02-01
Hi

Post the output of...

```
ls -l /etc/network/interfaces
lsattr /etc/network/interfaces
```

One of the suggestions in the thread i linked suggested using chattr +i ... Did you use that ?

Kind regards

---

### Post by lisati on 2011-02-01
Whoa! Isn't it the router's job to hand out IP addresses?

---

### Post by matt_symes on 2011-02-01
Hi

> Whoa! Isn't it the router's job to hand out IP addresses?


I was under the impression the server was receiving a DHCP address but was set to use a static address. 

I may have well missed something here so @OP can you clarify please.

Kind regards

---

