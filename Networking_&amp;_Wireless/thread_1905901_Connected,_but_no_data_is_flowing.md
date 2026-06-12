---
title: "Connected, but no data is flowing"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by n96 on 2012-01-07
I have Ubuntu 11.10 on a desktop pc. I bought an ASUS USB-n13 wireless adapter today. I plugged it in and connected, but even though I am connected to the router, all the programs are unable to actually reach any website. They recognise that there is an Internet connection, but they can't actually do anything. I am running pretty much the bare bones version of 11.10 Ubuntu (w/o any updates, just what comes with the installation package). Thanks for your help beforehand.


Addition: I am actually connected to the Internet - my pc has been assigned an IP. Also I think it might be a permissions issue of some sorts (as in if there is a firewall or something).

---

### Post by jsra on 2012-01-08
Hi,
does other kind of connection instead of web browser work?
Try
```
ping 8.8.8.8
```

---

### Post by n96 on 2012-01-08
The ping succeeded, other programs (software centre, updates, Ubuntu one, not even open ttd) are not working. The ping to 8.8.8.8 had 90% packet loss.

EDIT: after trying again, pinging resulted in 7% loss. Pinging my router resulted in 11% loss.

EDIT2: it is working now, but I'm still getting around 10% loss.

---

### Post by jsra on 2012-01-08
90% packet loss is kinda hard to troubleshoot. Now try to ping some site, eg. ```
ping www.google.com
``` Problem can be with nameserver(s) in your /etc/resolf.conf. Whats your signal quality? Can you get some closer to the router?

---

