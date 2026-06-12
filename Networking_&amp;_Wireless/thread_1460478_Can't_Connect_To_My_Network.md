---
title: "Can't Connect To My Network"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by cppnewb on 2010-04-22
Hi. I just installed Ubuntu 9.10 today. I am TOTALLY new to the Ubuntu world, and the first thing that happened was my the OS not picking up my wireless network. I am running a compaq presario c306us. I would greatly appreciate it if someone would help me diagnose and fix the problem.

Thanks in advance!

---

### Post by The Thunder Chimp on 2010-04-22
You probably don't have your Hardware Driver installed. Try going to System>Administration>Hardware Drivers. You should see a Hardware Driver free to download (do this with a wired connexion if possible), mine was B43. Install and download that and tell us how it went.

---

### Post by cppnewb on 2010-04-22
I went to the path that you specified over a wired connection and nothing showed up. It had a screen that said "No proprietary drivers are in use on this system"

---

### Post by bkratz on 2010-04-22
> **cppnewb said:**
> I went to the path that you specified over a wired connection and nothing showed up. It had a screen that said "No proprietary drivers are in use on this system"

The next thing to do would be to go to the terminal
(Applications>>Accessories>>Terminal) and enter in

```
lspci | grep Network
```

that is LSPCI in lowercase and N in upper. If you get no output try just lspci and look for the one which says network. Copy/paste the findings back here or decode it and report.

---

### Post by waptug on 2012-03-08
I am at this point as well.  I have gone on to the download and install of the bcm43 drivers
I activated the sta driver in additional drivers.
Did a restart
No Joy.
My presario had a little wifi button on it that manually turns the wifi on and off. 
It lights up an led in windows but the button does not work in linux.

I have following hardware:

Compaq Presario C306US
Broadcom BCM4311 802.11 b/g [14e4:4311] (rev01)
Ubuntu 11.10 freshly updated 

Just wondering if the little button is the problem.

---

### Post by waptug on 2012-03-08
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

I followed the info on this page.

Still not getting the WiFi to recognize it can work.

---

