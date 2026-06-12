---
title: "e1000e driver 0.3.3.3-k6"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by npoppeli on 2009-02-08
I have a problem with the Intel 82562V-2 network card in my Dell Vostro 200. This card requires the e1000e driver. When I run kernel 2.6.24 (driver version 0.2.0) the network card works fine 100% of the time. When I run kernel 2.6.27 (driver version 0.3.3.3-k6) chances are 50/50 that the network card gives trouble. 

Symptoms of the problem are: (1) even before there is a login prompt, there is considerable activity on the eth0 device; (2) getting an IP address through DHCP (normal mode of operation on my home LAN) is impossible; (3) manual configuration of eth0 is possible, but then the network is excruciatingly slow. 

[Update: appears to be related/identical to [kernel bug 11998]("http://bugzilla.kernel.org/show_bug.cgi?id=11998").]

Any suggestions or pointers are appreciated!

---

### Post by sully101 on 2011-09-22
I am still having this problem, did you find a solution?

refer [http://ubuntuforums.org/showthread.php?p=11276613#post11276613]("http://ubuntuforums.org/showthread.php?p=11276613#post11276613")

---

### Post by praseodym on 2011-09-22
Hi,

please check

```
dmesg | grep e1000
```
and maybe this site:

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

---

