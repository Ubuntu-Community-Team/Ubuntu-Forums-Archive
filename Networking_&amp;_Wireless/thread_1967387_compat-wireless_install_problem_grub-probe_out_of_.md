---
title: "compat-wireless install problem: grub-probe: out of  partition"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by cpk011 on 2012-04-28
Hi.
 
I am trying to build and install atl1c to fix my wired network connection problem on Ubuntu 10.04. I downloaded the latest compat-wireless file and was able to build atl1c. 
 
However when I tried to make install, it fails with the message:
 
/usr/sbin/grub-probe: error: out of partition
 
What do I need to do?
 
Thanks.
 
Peter

---

### Post by praseodym on 2012-04-28
Did you ever clean up your system?

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```
No need to compile (imho), install the "backport-modules" from synaptic

---

### Post by cpk011 on 2012-05-02
Thanks.
I realized that my problem with wired network connection was due to the faulty network cable rather than a network driver.
Peter

---

