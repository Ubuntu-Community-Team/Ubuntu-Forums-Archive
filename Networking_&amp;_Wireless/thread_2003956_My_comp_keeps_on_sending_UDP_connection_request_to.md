---
title: "My comp keeps on sending UDP connection request to itself?"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by supr1 on 2012-06-14
Every 31 secs, there is a new message in my system log like this:

kernel: [ 3169.740253] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.1 DST=192.168.0.255 LEN=217 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=197 

My ip addr. is 192.168.0.1 (netmask = 192.168.0.255)
What does that mean? 
Hlp pls.

---

### Post by Charlietje on 2012-06-15
> **supr1 said:**
> Every 31 secs, there is a new message in my system log like this:

kernel: [ 3169.740253] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.1 DST=192.168.0.255 LEN=217 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=197 

My ip addr. is 192.168.0.1 (netmask = 192.168.0.255)
What does that mean? 
Hlp pls.

By default, a CUPS network server broadcasts its queue every thirty seconds via the UDP port 631

---

### Post by supr1 on 2012-06-18
So, nothing to worry about that. What I know is that CUPS is print server. Will it send broadcast of its quee even there is no printing quee?
Thanks

---

### Post by Charlietje on 2012-06-18
> **supr1 said:**
> So, nothing to worry about that. What I know is that CUPS is print server. Will it send broadcast of its quee even there is no printing quee?
Thanks

Nothing to worry about.

If you don't use a printer you can stop the service

```
sudo service cups stop
```


If you want it to be removed as a start up service

```
sudo update-rc.d -f cups remove
```

---

### Post by supr1 on 2012-06-18
Thankyou. Would you tell me which sites good and easy enough to learn Ubuntu from?

---

