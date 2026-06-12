---
title: "Unable to receive multicast"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by de.lansier@gmail.com on 2011-06-23
For the last couple of days, I've been unsuccesfully trying to receive multicast packets on Ubuntu Server 11.04, and seen some strange things along the way. The program i use to test this, is basically [http://www.scribd.com/doc/38224328/mcreceive-c](http://www.scribd.com/doc/38224328/mcreceive-c).

Now the network has been configured to forward me the multicast packets, regardless of the joins. So tcpdump shows me:

```
15:16:11.308952 IP 10.164.130.2.61417 > 224.16.17.23.47806: UDP, length 1400
...

```However, after starting the test program, the multicast packets magically disappear from the tcpdump output, which seems to be a very strange side-effect. 

At the same time, the "recvfrom" call in mcreceive.c however blocks and returns no value. 

I verified that the interface has joined the group:

```
netstat -g | grep 224.16.17.23
eth3            1      224.16.17.23
```And that i'm listening on the right port:
```
netstat -l | grep 47806
udp        0      0 *:47806                 *:*
```Searching the forum, i found that the rpfilter might be an issue, so i disabled it:
```
 cat /proc/sys/net/ipv4/conf/*/rp_filter
0
0
0
0
0
0
0

```Anybody any thoughts on where else i could look for a solution ?

Thanks,
Steven

---

### Post by Lou66 on 2011-06-24
I think you have to use IP_ADD_SOURCE_MEMBERSHIP instead of IP_ADD_MEMBERSHIP and mention also the source IP address of the sender

---

### Post by de.lansier@gmail.com on 2011-06-28
Indeed,

Thanks !

---

