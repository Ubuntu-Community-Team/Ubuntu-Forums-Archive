---
title: "Traffic Shaping"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by CyberPingU on 2011-10-13
Hello all, I've read all the lartc documentation and even the htb's one.
Still I don't figure how to solve this.
I have a router with 3 interfaces:
[LIST=1]
[*]**eth2**: is connected to the ISP, and it's bandwidth is 4mbit/s in upload and 4 in dowload;
[*]**eth0**: is the LAN;
[*]**eth1**: is the DMZ
[/LIST]
I would like to share the 4mbit/s connection between the eth0 and eth1, letting one have, let's say, 1/3 of the total bandwidth, and the other one 2/3. When one doesn't use all the bandwidth it was assigned to, then it can borrow it to the other interface.
Since qdisc attaches to a device and works only in upload, I don't have a clue how to do to achieve this.
Is there a way?

---

