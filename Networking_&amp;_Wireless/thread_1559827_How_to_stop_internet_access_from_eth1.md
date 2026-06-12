---
title: "How to stop internet access from eth1?"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Josh1 on 2010-08-24
Hi All,

I have a bit of a "unique" situation here. I have myself plugged into two networks - since we run two networks here at work (long story, we merged and never combined them due to two different companies) and want to block ALL internet access off eth1, and only have it off eth0.

I only want traffic from 192.168.67.1-192.168.67.255 allowed on eth1, but everything allowed on eth0.

Or is there a way for the internet/applications to be on eth0 instead of eth1? Would I use iptables or something?

---

### Post by utnubuuser on 2010-08-24
would that be something along the lines of > sudo ifdown eth1
or, right-click the network icon, select "edit connections" and remove/edit eth0 or eth1

---

### Post by Josh1 on 2010-08-24
> **utnubuuser said:**
> would that be something along the lines of 
or, right-click the network icon, select "edit connections" and remove/edit eth0 or eth1

I want to use both network cards, since I need to connect to the Windows Server for development (building a web application with LDAP, and need to connect to the Windows Server to test authentication etc).

I just only want it to work internally.

---

### Post by Iowan on 2010-08-24
Just thinking out loud...
Routing could send all 192.168.67.X traffic to eth1, and eth0 could be the default for everything else - but that doesn't sound exactly like what you described...

---

### Post by dtoronto on 2010-08-24
Not sure exactly what you are trying to do, but you can set your default gateway to the interface that you would like to run your internet over which will force requests out that NIC but still allow incoming requests over the other.  Are both NIC's connected to the same gateway?  Are you trying to block all traffic from one NIC?

---

