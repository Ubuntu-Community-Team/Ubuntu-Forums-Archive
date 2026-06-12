---
title: "Ubutu Server 12.04 - network UNCLAIMED after reboot"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by mobo on 2013-05-23
I did a couple ofupdates, changes the ssh port as well s the webmin port then installed Denyhosts. After a reboot, the server has no connection. I did an "lshw -c network and the resulting card shows up but its header says its unclaimed..Any dieas on a fix?

---

### Post by linuxtechguy on 2013-05-23
Try:

ifconfig -a
cat /etc/network/interfaces

---

### Post by mobo on 2013-05-23
Thanks for the look.

Everything looks as normal as can be there with the exception for the packet entries. They are all zeroes.. However, it cannot be seen on the network nor go on the internet.

---

### Post by mobo on 2013-05-23
Got it..What I did was re-install the drivers that were in the home directory from the time I installed them. Then rechecked the /etc/network/interfaces file and changed  that to reflect the eth1 that changed from eth0. Rebooted and it came up..

---

