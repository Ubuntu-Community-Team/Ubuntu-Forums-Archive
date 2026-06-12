---
title: "assigning ip address to eth0"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by bsree on 2012-06-16
i am running #20 ubuntu. I've been trying to configure the ip address to eth0, but i keep getting these errors 

SIOCSIFFLAGS: No such file or direcotry.

#sudo ifconfig eth0 1.1.1.1 netmask 255.255.255.0
SIOCSIFADDR: File exists
SIOCSIFNETMASK: Cannot assign requested address

#sudo ifconfig eth0 up
SIOCSIFFLAGS: Cannot assign requested address

the nic card is not connected to a hub or switch. Is that the
reason why i'm getting these errors ?

---

