---
title: "Unable to communicate with local IPs when Private/Public IPs are specified"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by cfrolander on 2009-07-21
I'm having an issue where if my server (Ubuntu Server 9.04 64bit, though I've had this issue before with others) where if I specify a Public and a Private IP address I am unable to access the Public IP address from other local machines. If I bring down the Private IP, the public then works locally. It seems as if adding a Private IP address breaks my public IP locally (public still works externally)


```
# The primary network interface
auto eth0
iface eth0 inet static
address 67.40.90.180
netmask 255.255.255.248
broadcast 67.40.90.183
gateway 67.40.90.182

auto eth1
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
broadcast 192.168.1.255

```Is there something I should be doing with routes perhaps? The only time I can get the public IP to work is when I: ifconfig eth1 down

Machines on the local network also report that the host is taking too long to respond when both IPs are active.

Thanks in advance for the help!

---

### Post by superprash2003 on 2009-07-21
when both interface are up.. post output of** route -n**

---

### Post by cfrolander on 2009-07-21
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
67.40.90.176    0.0.0.0         255.255.255.248 U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         67.40.90.182    0.0.0.0         UG    100    0        0 eth0

```

So here's what I am wondering might be happening when both interfaces are up:

When a different machine 192.168.1.5 sends a message to 67.40.90.176, the server receives the packet and realizes that it can return it through 192.168.1.0 very easily (being on the same subnet) so ends up sending the response on the second (local) adapter and changing the IP address in the process.

This way, the client sends a request to .90.176 and get the response from .1.100, thus ignoring it and timing out.

I'm not a network guy by any means but this is what I was thinking might be causing this problem.

---

### Post by superprash2003 on 2009-07-22
have you tried bridging the two interfaces?

---

### Post by cfrolander on 2009-07-23
No I haven't, I'll give that a shot when I get home tonight.

What is the theory behind that? I am familiar with the term, but not familiar with how it might handle traffic differently in my situation.

---

### Post by superprash2003 on 2009-07-24
[http://en.wikipedia.org/wiki/Bridging_%28networking%29](http://en.wikipedia.org/wiki/Bridging_%28networking%29) .. basically forwards all traffic from one itnerface to the other

---

