---
title: "Broadcom STA wireless driver question"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by ranfan on 2012-03-17
I've installed it multiple times with no problem but during those times I had access to an ethernet connection. I was hoping there was a way to install it without one. I have a connection to the internet on another pc and was wondering if I could use that to download it and transfer it to the pc without an internet connection and install it while I'm offline.

---

### Post by ts3 on 2012-03-17
> **ranfan said:**
> I've installed it multiple times with no problem but during those times I had access to an ethernet connection. I was hoping there was a way to install it without one. I have a connection to the internet on another pc and was wondering if I could use that to download it and transfer it to the pc without an internet connection and install it while I'm offline.

This file has an explanation how to install the STA driver and the b43 driver without internet access: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx).  I reckon it will depend on which wireless card you have to figure out which driver you need.  

Some time ago I installed the STA driver without wireless following the guide I linked to, with some tweaks, on a 10.04 partition (the install worked but the wireless connection was very weak).  

I've also installed the wl driver without wireless (this is the driver which works best with my broadcom BCM4313 card but which is alas proprietary).  The driver and instructions are here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  I've described both installs in a thread I started a while ago.  

Again, what you need to do may be different, depending on the exact type of Broadcom card you have and the ubuntu version you have installed (in my experience, the STA driver on 11.10 works differently from the STA driver on 12.04).

---

