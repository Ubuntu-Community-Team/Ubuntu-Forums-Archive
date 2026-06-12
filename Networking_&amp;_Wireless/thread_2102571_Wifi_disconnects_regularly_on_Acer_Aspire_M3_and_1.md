---
title: "Wifi disconnects regularly on Acer Aspire M3 and 12.04"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by patrice079 on 2013-01-07
Hello,

I found some other threads with similar problems, but no solution helped in my case.

I have a new Acer Aspire M3 and installed Ubuntu 12.04 but my wifi connection disconnects every 5 minutes. I tried to follow this tips from other threads:

> 
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1


This:

> 
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source


I tried to uninstall network manager and install wicd, but nothing really helped.

I would be very happy if someone here could help me with this problem, it's really annoying to have an unstable wifi connection :(

---

### Post by WilhelmZantow on 2013-01-07
I have the same or similar problem with 12.04 on an ASUS M5A97 LE R2.0. The system works correctly hard wired.  In wirless mode the WEP key is accepted----a wirless connection is made----within seconds the connection is lost and key is re-requested---and the cycle repeats again and again.

At someones suggestion I went to "Network--Wireless--Options--Wireless Secuity (tab)--entered the WEP key--and clicked Save.(apparently the "save" locked in the WEP key)   That seemed to permenantly lock in the Key and we stayed on line. 

Now----PROBLEM # 2----The connection ran at about 5% of the hard wired system speed! Go figure! My second Desk Top with 10.04 running on the same router works perfectly. If you are really new and just want a good, plain, reliable Op System, Ubuntu !0.04 is a beauty---BillZ

---

### Post by Hadaka on 2013-01-07
Hi, when you disable 11n, does it stay online untill
you boot or restart?
IF yes..then see this thread...post #4

[http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable%3D1](http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable%3D1)

---

### Post by WilhelmZantow on 2013-01-08
BillZ here again
 ----Update----I loaded 10.04 alongside 12.04.----No wireless problem at all with 10.04. (with linux 2.5.32-45)-----12.04 problem is the same as in previous post (with Linux 3.2.0-35)   The "Linux 3.2.0-45" did not require a proprietary driver.  The equivalent "Broadcom B43 proprietary" required for 10.04 and that works, is apparently built into Linux 3.2.0-35.   
------My version of this problem would seem to be a Broadcom/Broadcom driver problem in Linux 3.2.0-35----Stay tuned ----I will install a different chip soon.----BillZ

---

### Post by WilhelmZantow on 2013-01-14
I don't feel any smarter but using a Sinmax SI-1500UG usb wireless device fixed the problem----it connected immediately----the WEP key was already stored somewhere from my previous activities----it ran at full speed-----{12.04 with linux 3.2.0-35}

Why the Broadcom wireless device worked perfectly in 10.04 but not in the later 12.04 is still a mystery.  The whole issue of wireless drivers and Linux based systems is something of a pain.  I have never had any trouble with drivers for other things.

BillZ

---

### Post by WilhelmZantow on 2013-01-15
One last blast----
1. A Sinmax USB wireless is my "Old Faithful" It has never not worked anywhere
2.  I installed a TRENDnet TWE_443PI PCI in the above system and UBUNTU 10.4, 12.4, and 12.10 all worked perfectly.
I would seem that the Linux versions* are not consistent relative to wireless drivers.  

*  10-04 Linux 2.6.32-45------12.04 Linux 3.2.0 -35-----12.10 Linux 3.5.0.-17**
**  This version {3.5.0 -17} does not report signal strength correctly but other wise works OK

---

