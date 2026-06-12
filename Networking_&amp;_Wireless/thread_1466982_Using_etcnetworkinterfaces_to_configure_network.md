---
title: "Using /etc/network/interfaces to configure network"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by ender8282 on 2010-04-30
How do I get *buntu to use the information in ```
/etc/network/interfaces
``` to set up my network connection?  I have .../interfaces correctly configured (for static ip) but every time that I boot up I acquire a dhcp address.  (It works but then I can't ssh into the machine.)  After booting up I can run 
```
sudo /etc/init.d/networking restart
```
and my network comes up with the expected static address from .../interfaces.  I tried uninstalling network-manager but then dns lookup failed.  

I have an ubuntu 8.04, and a 9.10 machine setup this way and they work great.  What has changed since 9.10?  Is it related to upstart taking over?

Thanks in advance for any help.

---

### Post by DGortze380 on 2010-04-30
Uninstall network manager and add your DNS entries to /etc/resolv.conf

---

