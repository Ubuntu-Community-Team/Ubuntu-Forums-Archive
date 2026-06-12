---
title: "how to display and remove my current wireless card modules"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2010-10-29
Hi, I need to try another modules for my wifi card, so I need to identify my current ones and remove them, so, here is my questions:

1. how can I display my currents wifi card modules?
2. what is the command to remove permanently?

regards

---

### Post by chili555 on 2010-10-29
Let me show you an example from my own computer:> sudo lshw -C network

*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       --- snip ---
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:49 memory:edf00000-edf00fffIt's much easier and a lot more effective to blacklist the module rather than remove it.```
sudo su
echo "blacklist [COLOR="Red"]iwl3945[/COLOR]" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by herbert tamayo on 2010-10-29
thanks for the reply, it was what i needed, just a comment:

the driver dislayed said "wl0", so I blacklisted as this, after reboot the card was up still, so, I checked with lsmod and found that the driver was "wl", kind of where for me, because "0" was as a parameter, but, blacklisted "wl" works good.

regards

---

### Post by chili555 on 2010-10-29
Those of us who study drivers will be interested in your result; that is, whether a better driver than *wl* exists for newer Broadcom cards. If you will, please keep us informed.

---

