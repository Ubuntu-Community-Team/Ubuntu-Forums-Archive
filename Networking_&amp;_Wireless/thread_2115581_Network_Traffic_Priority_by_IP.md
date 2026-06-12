---
title: "Network Traffic Priority by IP"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by goocreations on 2013-02-13
I'm looking for a way to shape network traffic based on the IP. I have a LAN, lets say from 192.168.1.2 - 192.168.1.254. The server is at 192.168.1.1. All IPs should have the maximum possible network speeds (all ports, but Samba is the actual culprit). The moment a specific IP or IP range (eg: 192.168.1.100) connects, the full speed should be given to that IP, all other IPs speed should be reduced to the minimum. Once the IPs traffic is finished, the rest of the connected IPs' speed should be restored.

I pretty much have a server and if my own PC connects to it, I want full speed. Only if I'm not using the server, the rest should have full access.

I've found some solutions online with **tc**, but they all limit specific IPs with a certain speed. I however want all people to have the max speed, except if a certain IP is connected. So basically my IP should have the highest priority and the rest the lowest priority.

Can anyone help me out with a script or maybe a program that already exists?

---

