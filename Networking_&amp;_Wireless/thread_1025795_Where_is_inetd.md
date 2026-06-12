---
title: "Where is inetd ?"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Biased turkey on 2008-12-30
I'm trying to install my HP C7200 ( all in one ) printer-scanner on my router-firewall that is also used as a file, printer and scanner server.
I don't have any problem with the printer part, the 2 other rigs on my network can use it.
The trouble is with the scanner.
I followed the Ubuntu scanning howto documentation but when trying to restart the inetd deamon I have the following message:

sudo /etc/init.d/inetd restart
sudo: /etc/init.d/inetd: command not found

What package should I get in order to have inetd installed ?
The only package listed by synaptic is "inetutils-inetd" is it the one I should install ?

Jacques

---

### Post by jpkotta on 2008-12-31
There is also xinetd, which is supposed to be better.  I don't get into the inetds enough to say if that is true or not.

---

### Post by robenroute on 2009-03-08
> **Biased turkey said:**
> I'm trying to install my HP C7200 ( all in one ) printer-scanner on my router-firewall that is also used as a file, printer and scanner server.
I don't have any problem with the printer part, the 2 other rigs on my network can use it.
The trouble is with the scanner.
I followed the Ubuntu scanning howto documentation but when trying to restart the inetd deamon I have the following message:

sudo /etc/init.d/inetd restart
sudo: /etc/init.d/inetd: command not found

What package should I get in order to have inetd installed ?
The only package listed by synaptic is "inetutils-inetd" is it the one I should install ?

Jacques

Yes, inetutils-inetd is something you could use. Just change the above command to restart to: sudo /etc/init.d/inetutils-inetd restart

Hope this helps.

---

