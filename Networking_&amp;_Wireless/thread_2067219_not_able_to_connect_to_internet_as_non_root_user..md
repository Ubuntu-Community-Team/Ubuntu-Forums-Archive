---
title: "not able to connect to internet as non root user."
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by sinbaddd on 2012-10-06
Hi, I just installed ubuntu 10.04, i'm not able to connect to
internet as a non root user. I can ping google.com if use sudo.
if i login as root i can connect to the internet. i even enabled the option of "connect to wireless and ethernet network" for the user in adminisration > users settings. how can i fix this.

-sinbad

---

### Post by Iowan on 2012-10-06
Is the interface set for "Available to all users" in Network Manager?

---

### Post by sinbaddd on 2012-10-06
> **Iowan said:**
> Is the interface set for "Available to all users" in Network Manager?

hi, i'm connecting through wireless-3g-dongle, in the ifconfig i saw it as a ppp0 interface, in nm-connection-editor i couldn't find this interface.

root@home-laptop:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
132.203.30.4    *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

---

### Post by sinbaddd on 2012-10-07
hi can someone help me out, there should be some option
which must be preventing me to connect to internet as non-root
user.

thanks

---

### Post by sinbaddd on 2012-10-14
can someone please help me out on how to solve this issue.

---

