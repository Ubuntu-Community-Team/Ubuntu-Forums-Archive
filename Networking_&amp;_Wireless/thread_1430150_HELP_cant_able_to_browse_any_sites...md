---
title: "HELP cant able to browse any sites.."
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2010-03-15
Its a single PC,i can ping my connection but i cant able to browse any sites..These are my outputs...

```
karthick@Learners-desktop:~$ ping -c 3 google.com
PING google.com (209.85.231.104) 56(84) bytes of data.
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=1 ttl=45 time=355 ms
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=2 ttl=45 time=355 ms

--- google.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2000ms
rtt min/avg/max/mdev = 355.239/355.534/355.830/0.665 ms
```

---

### Post by lrcaballero on 2010-03-15
Try this: in a terminal

Code:
ifconfig release

ifconfig renew

then try connecting and see what happens.

---

### Post by karthick87 on 2010-03-15
```
karthick@Learners-desktop:~$ sudo ifconfig release
release: error fetching interface information: Device not found
karthick@Learners-desktop:~$ sudo ifconfig renew
renew: error fetching interface information: Device not found

```

---

### Post by adam814 on 2010-03-15
Have you tried more than one browser?  Are you running a firewall?

Could you post the output of "sudo route -n"?

---

### Post by karthick87 on 2010-03-15
Output of **route -n**

```

karthick@Learners-desktop:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.96.136.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

### Post by mikemelen on 2010-03-15
Any proxy server configured there for access the internet?? 
like squid etc

---

### Post by karthick87 on 2010-03-15
Yes i am using squid to restrict some sites..

---

### Post by mikemelen on 2010-03-15
ok then give the proxy server details to your browser. 

in firefox select Menu >> Edit >> Preferences >> There select Advanced 

In connection settings select manual proxy configuration and give your squid server ip and port number

---

### Post by karthick87 on 2010-03-15
Proxy settings were good,and my connection works fine till yesterday..I haven't changed anything but all of a sudden i cant browse any sites..

---

### Post by mikemelen on 2010-03-15
have u checked the access and error log of proxy server, by verifying that file we can find out the exact issue. Also can you access the local system over browser.

---

