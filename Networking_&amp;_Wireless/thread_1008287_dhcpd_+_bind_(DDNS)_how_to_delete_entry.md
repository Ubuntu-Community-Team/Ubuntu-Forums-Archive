---
title: "dhcpd + bind (DDNS) how to delete entry"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by b4nsh33 on 2008-12-11
Hi, i have a several computers that use dhcpd to get its ip address, the dhcpd daemon then updates the bind zone accordingly, so far so good, my problem is that from time to time i need to delete that entry, so, pc1.myzone.com its not pointing to 192.168.10.120 anymore, now that ip is pointing to pc2.myzone.com (dont ask me why , its out of my control, sales department insists in randomly change the computers name, and beacuse dhcpd uses the mac address, no new ip is assigned).
What is the recommended way to this? 
Right now what i do is to delete the entry in dhcpd.leases and to update the bind's zone file, then restart both services.
is there a command line utility for this?
best regards

---

