---
title: "Broadcom STA Wireless drivers not working on Dell Inspiron 1750"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by Nate2012 on 2012-07-11
I need help!!
 
After upgrading to kernel 3.4 in Ubuntu 12.4, all of a sudden my wireless capabilities have stopped. I've tried searching for additional drivers, but when I do, this is what I get back: Sorry, installation of this driver has failed.
 
Please have a look at the log file for details: /var/log/jockey.log
 
 
I've run this command in the terminal:
 
lspci -nn | grep 0280
 
This is the information I got back: 
 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
 
 
I would really appreciate the help on this!!!!

---

### Post by praseodym on 2012-07-11
Did you also install the corresponding "header"-files from that site? Plus afterwards

> sudo apt-get install --reinstall dkms patch fakeroot bcmwl-kernel-source

---

### Post by Nate2012 on 2012-07-13
Thanks for trying to help, but I just decided to reinstall Ubuntu and now everything is up and running fine.

---

### Post by Nate2012 on 2012-07-13
> **praseodym said:**
> Did you also install the corresponding "header"-files from that site? Plus afterwards
 
Thanks for trying to help, but I just decided to reinstall Ubuntu and now everything is up and running fine.:)

---

### Post by NoBugs! on 2012-08-08
You need to select the older kernel in the boot menu, to bring back the wifi. Then uninstall the newer kernel with Synaptic.

I have the same problem, the above command didn't solve the problem for me either, unfortunately, but it did make the wifi work again after I uninstalled the newer kernel and rebooted into the normal one.

---

