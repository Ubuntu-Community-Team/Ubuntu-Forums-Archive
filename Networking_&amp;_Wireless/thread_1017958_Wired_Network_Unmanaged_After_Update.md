---
title: "Wired Network Unmanaged After Update"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by beers on 2008-12-21
Updated my 8.10 server install yesterday, and now I seem to be having problems with Networkmanager in gnome.  Networkmanager tells me device eth0 is unmanaged, but I can't seem to get it to fix.  I have a static IP on a DHCP network that has been working alright, but now my samba name resolution is not functioning as it did before the update.  I have tried to comment out eth0 in /etc/network/interfaces.  Upon reboot, networkmanager recognized and attempted to manage the device.  After putting it on DHCP the server would obtain an IP, however no applications can utilize the interface.  Whenever I try to ping another IP it tells me Operation not permitted.  Any thoughts? :confused:

---

### Post by beers on 2008-12-21
Looks like IPtables got 'adjusted' somehow.  

sudo iptables -F

Works.  Thanks.

---

