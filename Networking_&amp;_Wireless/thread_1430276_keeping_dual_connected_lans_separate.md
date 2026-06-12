---
title: "keeping dual connected lans separate"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Highway on 2010-03-15
Hi,
I have an Ubuntu 9.04 server running Bacula for our backups with two Nics.  One is connected to the corporate lan, and one is connected to a lan dedicated to the backup traffic.  This NIC is connected to a dedicated switch for the bacula lan traffic and each server being backed up has an interface connected to this switch.  The backup lan has it's own subnet, and each servers Backup NIC has an ip address on that subnet.  

I want these two lans to remain completely separate, but at the moment i can ping the backup lan from any device connected to the corporate lan (who are no connected to the backup lan).

I am concerned that some backup traffic may travel over the corporate lan, or that servers that are dual connected may route the wrong way. 

How do i stop the backup lan from being visible on the corporate lan?  I presume the Ubuntu server is advertising it's existence to the corporate lan through that NIC in some way.  

Thank you.
Highway.

---

### Post by suseendran.rengabashyam on 2010-03-16
Hi,

Open the file /etc/sysctl.conf and add the following two lines

net.ipv4.conf.all.arp_ignore=1
net.ipv4.conf.all.arp_announce=2

save and close the file.

Reboot the machine for the changes to take effect.

Hope this helps.

---

