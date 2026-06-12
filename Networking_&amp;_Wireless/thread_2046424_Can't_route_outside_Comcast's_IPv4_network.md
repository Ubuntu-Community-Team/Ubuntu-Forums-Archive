---
title: "Can't route outside Comcast's IPv4 network"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by danry25 on 2012-08-22
Hey, I have a Ubuntu 12.04 x64 Desktop install, and it will repeatedly refuse to route to any IPv4 address outside my local lan or Comcast's network. Occasionally I will just sshuttle into a server at my friends house (he also has comcast) and I'll be able to  access the Internet without issue. When this issue is occurring I will  be able to ping only Comcast or Lan IPs, and if I switch to tethering off my phone the issue will dissappear. Rebooting will help temporarily, but only about 25% of the time. 

 While this is all going on with my desktop, all of the servers (which are also running Ubuntu 12.04) can access the Internet along with the Windows computers, Androids & iPhone in the house. Also, if I go & grab another laptop running Ubuntu 12.04 it has the same issue. I have tried rebooting my modem, router, swapping both out, etc. This issue also appears at other places such as at friends houses, where if it is occuring it will affet all Ubuntu 12.04 desktop installs that are connected to that particular router.

This whole issue seems to be fleeting, yet I can't find a reliable way to resolve it.

---

### Post by sandyd on 2012-08-22
Can you post the output of
```

route -n
```
You might need to add sudo in front

---

### Post by danry25 on 2012-08-22
It appears to have resolved itself, but I will most likely run into this  issue again tomorrow. Let me dump a working route -n while things are  working right though, I'll reply with a route -n next time this crops  up.

Working:
user@User:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
user@User:~$

---

### Post by danry25 on 2012-08-23
An now it stopped working, here is the result of route -n:

user@User:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
user@User:~$ 


Looks the same to me, any other commands I should run?

---

