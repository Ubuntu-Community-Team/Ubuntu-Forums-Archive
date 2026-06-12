---
title: "DHCP issues?"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by hunter.allen on 2012-07-16
Having trouble with dhcp assignment... 


```
allenh1@roboard:~/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3621
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1b:eb:43:37:ce
Sending on   LPF/eth0/00:1b:eb:43:37:ce
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 129.59.90.16 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 4270
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:12:7b:43:3a:f5
Sending on   LPF/eth1/00:12:7b:43:3a:f5
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 129.59.90.16 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1b:eb:43:37:ce
Sending on   LPF/eth0/00:1b:eb:43:37:ce
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 129.59.89.40 from 129.59.88.1
DHCPREQUEST of 129.59.89.40 on eth0 to 255.255.255.255 port 67
DHCPACK of 129.59.89.40 from 129.59.88.1
bound to 129.59.89.40 -- renewal in 2905 seconds.
ssh stop/waiting
ssh start/running, process 4477
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:12:7b:43:3a:f5
Sending on   LPF/eth1/00:12:7b:43:3a:f5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 4588
```

Any idea as to why I get no dhcp? 

Thanks, 
-Hunter A.

---

### Post by papibe on 2012-07-16
Hi hunter.allen.

Could you give us a little more information.

Is this a server or a desktop?
If it is a desktop, did you uninstall network-manager?

My first guess is that either your router or DHCP server is down:
```
No DHCPOFFERS received.
```

Regards.

---

### Post by TheFu on 2012-07-16
If the router or DHCP server is up, perhaps there aren't any more available leases? Did you restrict the number of DHCP leases available?  To force this to be cleared, it is often easiest to reboot the home router. In a business, that isn't usually possible.

If this is an issue at a company with a non-trivial network, they might be out if leases. You'll need to contact the helpdesk and have them check the AD/DCHP server.

---

### Post by papibe on 2012-07-16
After a second look (thanks chili555), I realized that you have 2 NICs, and you are running trying to get addresses for the same network on them.

If so, I wouldn't recommended it.

Could you please give us more information on what you are trying to accomplish? 

Regards.

---

