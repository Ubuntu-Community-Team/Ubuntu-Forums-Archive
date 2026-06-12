---
title: "Backend crashing when doing autoexpire"
date: 2009-10-17
forum: Mythbuntu
---

### Post by sydneysuder on 2009-10-17
Hi, 
Everyday around the same time I have to re-start the backend. I had a look at the logs and there is an "IPMEMBERSHIPERROR" when it is trying to do the auto expire.  I am not sure where to look.


Any help is greatly appreciated
[http://mythbuntu.pastebin.com/f5d83825](http://mythbuntu.pastebin.com/f5d83825)



[INDENT]==> /var/log/mythtv/mtd.log <==
mtd started at Fri Oct 16 11:43:28 2009
mtd is running on a host called mythserver1
11:43:28: Waiting for connections/jobs
11:43:28: mtd is listening on port 2442
 
==> /var/log/mythtv/mythbackend.log <==
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
2009-10-17 15:14:59.258 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-10-17 15:17:05.824 UPnpMedia: BuildMediaMap VIDEO scan starting in :/video/videos:
2009-10-17 15:17:05.833 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-10-17 15:29:59.287 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-10-17 15:44:32.181 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket
QSocketDevice::sendBlock: Invalid socket/INDENT]

---

### Post by ian dobson on 2009-10-17
Hi,

Are you using upnp on your backend. If not disable it by editing the file /etc/default/mythtv-backend and changing the line EXTRA_ARGS=  to read EXTRA_ARGS=" --noupnp ".

Regards
Ian Dobson

---

### Post by sydneysuder on 2009-10-20
I was using UPNP but after tying adding a route it did not fix the problem. So I am turning it off and seeing what happens.

---

### Post by sydneysuder on 2009-10-23
OK. That worked. 
The thread can be marked as solved.

---

