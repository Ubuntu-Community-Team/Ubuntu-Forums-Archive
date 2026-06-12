---
title: "No route to host"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2010-09-09
nuno@sky9:~$ telnet 192.168.1.1
Trying 192.168.1.1...
telnet: Unable to connect to remote host: No route to host
nuno@sky9:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


Is this error message possible as the routing table have a entry for that IP range?
I have to disconnect and reconnect the ethernet cable several times until I get a connection...
Ping also fails, so it is not a telnet issue.


Ubuntu 10.04, all updates
nuno@sky9:~/trunk$ uname -a
Linux sky9 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

---

