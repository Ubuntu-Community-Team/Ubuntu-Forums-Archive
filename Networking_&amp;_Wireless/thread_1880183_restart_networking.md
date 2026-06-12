---
title: "restart networking"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by cropr on 2011-11-13
I am trying to setup my ubuntu 11.10 as a dhcp-server and this is a kind of nightmare.  After installing dhcp3-server I get on error message I can apparently ignore (some work is needed here for the dhcp3-server package maintainers).  

I've configured /etc/dhcp3/dhcp3.conf and /etc/default/dhcp3-server, now I need to restart networking but I cannot find the way to do this (apart from a reboot)

```
/etc/init.d/networking
``` restart does not do the job anymore
```
stop networking
```  and then ```
start networking
``` leaves the networking in a unconfigured state

Any help

---

### Post by ajgreeny on 2011-11-13
Try ```
sudo service networking start
```It may need to be started with root permissions.

---

### Post by cropr on 2011-11-13
If I do that I get the error "restart: Unknown instance"

---

