---
title: "Dell Studio 1558 ubuntu No wireless net"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by 83RN15 on 2013-02-10
Hi, i just recently started using ubuntu im a total noob at this linux stuff

but the os was working perfectly, after i did an update it was asking me to do, wireless network stoped working, it wont identify any.

**Version of ubuntu: 12.10 64 bit**

---

### Post by 83RN15 on 2013-02-10
tried what was posted in this thread worked
[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

ran the following commands in the terminal and rebooted it worked fine.
>  			 				sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter 			 		

---

### Post by kc1di on 2013-02-10
give the instructions on [this page]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working"). a try think it will work for your card.

---

