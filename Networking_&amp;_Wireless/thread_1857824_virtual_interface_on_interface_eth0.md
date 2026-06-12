---
title: "virtual interface on interface eth0"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by vikas.byn on 2011-10-11
I create a virtual interface on interface eth0.

eg. mechine 1 and mechine 2 have ubuntu as OS

at mechine 1:

# ifconfig eth0:1 172.16.105.1 netmask 255.255.255.0

and then check - # ping 172.16.105.1 
it will give icmp reply and then i check a port on this virtual interface.

# nc -vz 172.16.105.1 22
Connection to 172.16.105.1 22 port [tcp/ssh] succeeded!

at mechine 2:

# ifconfig eth0:1 172.16.105.1 netmask 255.255.255.0

and then check - # ping 172.16.105.1 
it will give icmp reply and then i check a port on this virtual interface.

# nc -vz 172.16.105.1 22
Connection connection refused.

SSHD is running on both mechine at their physical interface.

mechine 2 is working fine. then what is the problem with mechine 1?

Please reply me soon..

---

