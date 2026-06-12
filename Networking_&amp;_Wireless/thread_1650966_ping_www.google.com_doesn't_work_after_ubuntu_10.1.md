---
title: "ping www.google.com doesn't work after ubuntu 10.10 installation"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by aj@ubu on 2010-12-22
Hello all, :KS
 
I installed ubuntu 10.10 today and when i open the browser it doesn't show any sites. I tried
 
> ping [www.google.com]("http://www.google.com")
ping : unknown host [www.google.com]("http://www.google.com")
 
> telnet > open localhost
Trying ::1...
Trying 127.0.0.1...
telnet : unable to connect to remote host : connection refused
 
______________________________________________________________________________
cat /etc/hosts
 
myip aj-HP-D530-CMT-DP3865 # Added by Network manager
127.0.0.1 localhost.localdomain localhost
::1 aj-HP-D530-CMT-DP3865 localhost6.localdomain6 localhost6
127.0.1.1 aj-HP-D530-CMT-DP3865 
_____________________________________________________________________________
 
cat /etc/nsswitch.conf
 
passwd: compat
group: compat
shadow: compat
 
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
networks: files
 
protocols: db files
services: db files
ethers: db files
rpc: db files
 
netgroup: nis
______________________________________________________________________
 
any ideas ?
 
- A

---

### Post by furlabs on 2010-12-24
Try pinging a real world IP:
```
ping 66.102.11.104
```
If that works, you have a DNS issue. If it doesn't, you have no internet.

If you have no internet, try pinging your local router/gateway. I don't know what the IP might be but something like:
```
ping 192.168.1.1
```

Let us know how you go and I will tell you what to try next.

---

