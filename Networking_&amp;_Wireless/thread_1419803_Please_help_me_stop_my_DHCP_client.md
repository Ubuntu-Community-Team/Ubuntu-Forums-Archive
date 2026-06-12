---
title: "Please help me stop my DHCP client"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by harisund on 2010-03-02
Hey people

I have Ubuntu server, so I don't have that NetworkManager stuff running. 

I have the following in my /etc/network/interfaces
```

auto eth1 
iface eth1 inet static
address 192.168.5.50
netmask 255.255.255.0
gateway 192.168.5.5
```

But I keep seeing the following in my /var/log/syslog```

Mar  2 09:06:35 Optiplex dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar  2 09:06:35 Optiplex dhclient: DHCPOFFER of 192.168.5.106 from 192.168.5.5
Mar  2 09:06:35 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 255.255.255.255 port 67
Mar  2 09:06:35 Optiplex dhclient: DHCPACK of 192.168.5.106 from 192.168.5.5
Mar  2 09:06:35 Optiplex dhclient: bound to 192.168.5.106 -- renewal in 1688 seconds.
```

WHY !!!! 

I have a router (obviously 192.168.5.5) and I have setup DMZ on that router to be 192.168.5.50 so that I can access my server from the outside world. If the stupid thing keeps getting an address in the DHCP subnet of the router, I can't access it from outside! 

When the computer boots up, it keeps the proper 192.168.5.50 address I have set it up. But every so often it just decides to activate the DHCP client and pick up a new address from the router. 

I have not yet looked into syslog to see if this happens at a regular interval. Perhaps a cron thing?

---

### Post by Barriehie on 2010-03-02
So you want to disable the dhclient???

---

### Post by harisund on 2010-03-02
If by 'disable' you mean stop it from randomly starting itself, yes. 

See, when I installed the server, I used DHCP. But later on, I remove the *iface eth1 inet dhcp* line and replaced it with *iface eth1 inet static* line. 

I don't want to uninstall it, no. Just stop it from randomly getting executed.

Honestly though, I want to know why this is happening ..

---

### Post by harisund on 2010-03-02
```

Mar  2 09:34:43 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 09:58:42 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 10:22:00 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 10:49:12 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 11:13:40 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 11:43:41 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 12:11:22 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 12:36:31 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 13:03:26 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 13:27:04 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 13:50:38 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 14:20:38 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67
Mar  2 14:49:20 Optiplex dhclient: DHCPREQUEST of 192.168.5.106 on eth1 to 192.168.5.5 port 67

```

Does anyone see any method to this madness? I tried do a grep DHCPREQUEST ... I am not able to find any regularity ..


But I am able to observe a few other things. One, after it acquires an IP it says -- *renewal in 1506 seconds* and the renewal happens after that much time. My next question, my router is set to provide DHCP leases for 1 hour. Why is my DHCP client acquiring a lease only for 30 minutes max?

---

### Post by Barriehie on 2010-03-02
Try finding the .conf file and comment out the request line.  Also might be bug related. [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/38140](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/38140)

---

### Post by pricetech on 2010-03-02
> **harisund said:**
> My next question, my router is set to provide DHCP leases for 1 hour. Why is my DHCP client acquiring a lease only for 30 minutes max?

That's the way DHCP is designed to work.  The client requests renewal in 1/2 the lease time.

Sorry I can't explain why the client is running in spite of having a fixed IP, but something else you might consider is reserving the IP in the router.  most routers allow you to reserve certain IPs from the pool for certain MAC addresses.  Just a thought.

---

### Post by Barriehie on 2010-03-05
So what's up with this harisund?  Did you get it???

Barrie

---

### Post by DGortze380 on 2010-03-05
sudo /etc/init.d/networking restart

---

### Post by gabak on 2010-07-20
write this and it will stop ur dhcp
ifdown eth0


There is already a pid file /var/run/dhclient.eth0.pid with pid 2040
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:d3:f2:35:bc
Sending on   LPF/eth0/00:13:d3:f2:35:bc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.10.0.78 port 67

---

