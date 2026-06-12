---
title: "Won't Connect to Ethernet."
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Kilroy94 on 2008-12-31
I clicked xubuntu, but meant ubuntu.
So i have 3 computers, and they work perfectly with the wireless, however when i try to connect any of them (one being a server), they all wont receive a valid IP Address. They are running Windows XP SP3, Ubuntu 8.04 and Ubuntu 8.10. Thanks,
   Kilroy

---

### Post by superprash2003 on 2009-01-01
check the DHCP range of your wifi router.. make sure it has sufficient range to provide ips for all machines.. if not try using static ip

---

### Post by Kilroy94 on 2009-01-01
And how would i go about doing this? Thanks.

---

### Post by Iowan on 2009-01-01
> **Kilroy94 said:**
> And how would i go about doing this? Thanks.Checking DHCP range, or setting static address?
I've only set up one router (A Dlink, as I recall), but most have a web-based setup page - usually at router's address (which is *probably* 192.168.X.1, where X is *probably* 0 or 1).
Static IP: [This]("http://ubuntuforums.org/showthread.php?t=974382") workaround may provide useful information.
Another option from the router setup - issue a static lease based on client's MAC address.

---

