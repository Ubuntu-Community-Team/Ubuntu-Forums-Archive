---
title: "Routing with two NICs"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by king vash on 2011-05-11
I live on a college campus where I run two separate media servers on my desktop. One is a samba server and the other an application called WASTE which uses port 1337. Both use approximately the same bandwidth.

the computer has two NICS connected to the school (both are 100mbits/s)
I have started to frequently (~30% of the time) saturate my primary link.

I would like to block all of port 1337 on eth1 but allow it on eth4.
I would also be interested in having Firefox use eth4.

Is there a simple way to do this?

I have been trying with route and iptable all night but with no success.

---

### Post by Drenriza on 2011-05-11
Why don't you use nic one to download with and nic two to upload with?

---

### Post by king vash on 2011-05-11
I have relatively low download but a huge amount of upload plus the connection is in full duplex mode.

---

