---
title: "Network Manager static IPs"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by cong06 on 2010-05-26
I have a few computers:
server
class1
class2
class3

I want to have static IPs so that I can manage content filtering on these computers (class1-3).
I think part of the issue is that these computers (class1-3) get turned on before the router (server).

here's the general "Auto eth0" file:
```

user@class1:~$ sudo cat /etc/NetworkManager/system-connections/Auto\ eth0 
[sudo] password for user: 

[connection]
id=Auto eth0
uuid=815eb3e7-868a-41f7-ae7e-78a62a2080fa
type=802-3-ethernet
autoconnect=true
timestamp=1274701092

[ipv4]
method=manual
dns=10.42.43.1;
addresses1=10.42.43.21;24;10.42.43.1;
ignore-auto-routes=true
ignore-auto-dns=true
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:1:03:16:d0:68
mtu=0

```
The only change is that each file has a different IP:
class1: 10.42.43.21
class2: 10.42.43.22
etc.

The problem is that they're getting different IP's, in the 10.42.43.1X group.
If I do "sudo ifconfig eth0 down; sudo ifconfig eth0 up" then the computer seems to get back on the right IP address... but why isn't it working right the first time?

---

### Post by cong06 on 2010-06-18
Do I have to go in manually and edit the "/etc/network/interfaces"?
I can't do this with network manager?

---

