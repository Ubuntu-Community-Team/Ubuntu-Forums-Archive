---
title: "kernel 2.6.27.9 and Broadcom bcm4312 and hp2133 mini note"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by cenwesi on 2008-12-15
I have an HP 2133 Mini notebook. It comes with the dreaded Broadcom bcm4312 [14e4:4312]. I have installed Ubuntu Intrepid v8.10 and updated to kernel 2.6.27-10 and the Broadcom proprietary driver installed. The Wireless worked flawlessly. 

Recently i decided to compile the kernel since i have the Via C7-M processor and after installing the Kernel, i can not seem to get wireless working. I will prefer to use the Broadcom proprietary driver rather than the ndiswrapper one. I have also tried System->Administration->Hardware Drivers and **no** Broadcom proprietary driver was listed. I have also tried the [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) driver released few days ago and could **NOT** get it to compile on my newly created kernel.

Please if anyone can show me how to get wireless working i will really appreciate it with kernel 2.6.27.9

Thanks in advance.

---

### Post by Ayuthia on 2008-12-15
You will not be able to use the module from Hardware Drivers because it was compiled for the Ubuntu kernel.  You will have to compile the wl driver on your own.  This [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61").  Since you compiled your own kernel, you will also need to make sure that ieee80211_crypt_tkip is also compiled.

---

