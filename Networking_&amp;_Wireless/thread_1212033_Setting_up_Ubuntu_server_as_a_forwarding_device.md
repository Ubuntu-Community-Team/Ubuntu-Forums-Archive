---
title: "Setting up Ubuntu server as a forwarding device"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Daimanta on 2009-07-13
I have an Ubuntu server together with a small amount of computers. The computers are given a fixed IP-address based on their MAC-address by our local uni. The situation now is that these computers are linked to a switch, which is linked to our university provider. 

The server has 2 physical ethernetports: eth0 and eth1. The internet connection is entering in my eth1 port. What I want to do is regulate all trafic through the server. The switch should go to eth0 and recieve communications from the server via the incoming connection via eth1. The computers need to be able to retain their original IPs and route normally otherwise. Is this possible?

---

### Post by superprash2003 on 2009-07-13
are you talking about internet connection sharing? if so , [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

