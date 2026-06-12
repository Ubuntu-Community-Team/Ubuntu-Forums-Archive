---
title: "Can't connect to secure wireless networks"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by gregalynch on 2013-01-31
As of last night, I can no longer connect to password protected networks.  When I turn the security off on my router, it will connect just fine.  But when I try to secure it -- using either WEP or WPA, the little wireless icon just scans and scans and never connects.

I've tried restoring the router to factory settings, changing the SSID, but nothing seems to work.

It would connect fine the night before last, and to my knowledge I haven't changed anything.

12.04 64 bit

EDIT: It seems that the problem might be specific to my router.  I can connect to a WPA protected network at work.  Is there something that would prohibit me from connecting to a specific router when password protected?  The problem doesn't seem to be with the router itself, because my wife's computer can connect to it fine, even when the security is enabled.

---

### Post by drbin on 2013-02-01
same here, to diff networks. have problem with WEP. On a WPA works with no problems. Happens just right after a kernel +others update. 12.04 LTS

---

### Post by srekcahrai on 2013-02-01
Try connecting to hidden wireless network and add network name and choose the wireless security type along with your password and connect.

---

### Post by drbin on 2013-02-01
just found this thread [http://ubuntuforums.org/showthread.php?t=2110149&page=4](http://ubuntuforums.org/showthread.php?t=2110149&page=4)

I used a usb wifi and connected. the problem IS on my Broadcom BCM4313 that happened just after the update I did today.

It does not feel right to me, to blacklist the driver as suggested in the thread listed above. Somethiing was not ok in the updates. It was working fine for months.

---

### Post by drbin on 2013-02-01
nope srekcahrai, no positive results.

---

### Post by srekcahrai on 2013-02-01
Have you installed proprietary  software for your wireless?

---

### Post by dnr1128 on 2013-02-01
I've had a similar problem with my laptop that has the 4313.  We have a Belkin N300 router and my system worked fine with it.  Software updater came up with a broadcom update, I downloaded and installed it.  Now the system WILL NOT connect to that router.  I purchased a Netgear N300, it connects and runs fine.  But, as I described in [this thread]("http://ubuntuforums.org/showthread.php?t=2111077"), things still aren't right.  I've even upgraded the entire system.  I've posted several questions on here, but so far I haven't gotten any responses.  I'm completely stumped, and it all started with updating that driver.

---

### Post by gregalynch on 2013-02-03
I do have the broadcom proprietary driver.  To my knowledge, though, it hasn't been updated anytime recently, and as I said, everything worked fine a few days ago.

Could the problem be with the router?  I tried to update the firmware on it, but it couldn't connect for the update (I think because the router is pretty old - ~7-8 years).

Currently I've just turned off the security on the router, and everything works fine.

---

### Post by drbin on 2013-02-04
[This]("http://ubuntuforums.org/showthread.php?t=2112259") solution worked at [http://ubuntuforums.org/showthread.php?t=2112259](http://ubuntuforums.org/showthread.php?t=2112259)

installing the older version of the driver. This bug really got me.

---

