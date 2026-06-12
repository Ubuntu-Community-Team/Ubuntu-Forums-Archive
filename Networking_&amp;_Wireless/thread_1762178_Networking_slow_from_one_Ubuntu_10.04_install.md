---
title: "Networking slow from one Ubuntu 10.04 install"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by faithfracture on 2011-05-18
Hey everyone. I'm not really sure what the deal is here. I've noticed that my network access is rediculously slow from one particular install of Ubuntu. I have Windows and another version of Ubuntu installed on the same machine which both work just fine. Something with the one installation is screwed up though and I really can't figure out what it is.

I noticed that when I do a /etc/init.d/networking restart I get all of this garbage that I haven't seen before (replaced my MAC with 'xx's):

```
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 1363
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.15 from 192.168.1.1
DHCPREQUEST of 192.168.1.15 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.15 from 192.168.1.1
bound to 192.168.1.15 -- renewal in 2147483648 seconds.
ssh stop/waiting
ssh start/running, process 2149

```

I haven't seen this before on any other Ubuntu installations I've done. Normally it just says something like "Stopping networking.... starting networking..." and that's it, so I'm not sure if whatever this is might have something to do with my problem or not. Is there something I might have installed that's causing this that I don't remember? I'd appreciate any thoughts.

Thanks.

---

