---
title: "Zonet ZEW2545 Wireless adapter keeps disconnecting"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Dbtm on 2011-06-02
Hello.

I got a Zonet wireless usb adapter ZEW2545 for my desktop running Ubuntu 11.04 that keeps connecting and disconnecting every minute. My two other laptops (running both Windows and Ubuntu 11.04) are able to connect to the wireless network without any problem. 

I installed the proprietary driver from the chip's developer's site, but when I go to system->administration->additional drivers it tells me the driver is installed but "not currently in use".

Could anyone help me on how to enable this driver?

---

### Post by Dbtm on 2011-06-04
Bump

---

### Post by IWantFroyo on 2011-06-04
Click on the driver, and then there should be a button saying "Activate" in the lower right hand corner.

---

### Post by Dbtm on 2011-06-04
Thanks for your reply! Actually, the driver is already activated, but somehow "not currently in use".

---

### Post by Dbtm on 2011-06-04
Well, it seems I finally got the thing working: 

I opened up /etc/network/interfaces and just erased all information about eth0 and wlan, restarted the PC and the adapter connected to the wireless network without problems.

The odd thing is that the proprietary driver still shows as "activated but not currently in use". But hey, it works now!

---

