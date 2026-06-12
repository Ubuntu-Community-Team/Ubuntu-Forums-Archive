---
title: "Can't get NAT to work in Hardy Heron"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Korhal on 2008-12-29
So far I have been reading Howto's and a lot of things about NAT in Ubuntu, none have worked out to solve my problem however.

I will try to give as much info about the problem I am having as possible.

I have a server it is running Ubuntu 8.04 Hardy Heron (Desktop Edition) which I know is perhaps not always the best choice for a server but shouldn't give too much problems. It has 3 NICs from which 2 are enabled.

eth0 = 172.16.1.2 (which is the internal LAN)
eht1 = 170.168.7.3 (which is the link to the router/modem of the ISP)

Internal LAN scope:
Network: 172.16.1.0
Subnet: 255.255.255.0 (yes it is subnetted with /24 to create subnets)
Gateway: 172.16.1.1 (This is unfortunately a Windows Server, but I has no choice for the time being)

Router Scope:
Network: 170.168.7.0 (wanted to change this, but for some reason the router does not allow it)
Subnet: 255.255.255.0 (also /24)
Gateway: 170.168.7.1 (Router, itself which connects to the internet)

I have a webserver and a variety of other servers in my internal lan. Herefore I must use NAT to make them available for the outside world, the NAT is currently being taken care of by the Windows Server, because I cannot get Linux NAT to work. I am also using webmin for the IPtables configuration, since I kind of lost track of all the rules in the file when I used the command-line. I do know the commands, though.

E.g.
Webserver = 172.16.1.4 port 80 proto TCP

I had input the following rule in the PREROUTING NAT table
```
iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 80 --to-destination 172.16.1.4:80
```

This didn't work.

What I have checked so far:

/etc/sysctl.conf
```
net.ipv4.ip_forward=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

I have tried:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
as well, it was no go.

What I will try now is to install the server kernel in the desktop edition to see whether that will solve the problem, but I doubt it.

I hope anyone here has a solution to this problem, the moment I will get this to work I will document exactly what I did to fix it and what I did wrong. 

Since I find the current Howto's that are available incomplete when it comes to this matter, they only describe an internet gateway not a server which must do NAT routing towards the internal network.

-----

As I expected changing the kernel to the server version didn't resolve anything at all, it still did not work.

I have also checked the kernel modules and whether my NAT module was loaded, it was. So far nothing worked and NAT still is not functional.

---

