---
title: "Asus Aspire V5 11.6&quot; mobile broadband problem"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by ilia_avramov on 2012-11-15
Hi boys,
yesterday I bought a new laptop- Acer Aspire V5 11.6". It came with Win7 pre installed. I have been using Ubuntu for 4 years and the first thing I did, was to partition HDD to install Ubuntu.Then I made a bootable flash-drive with Ubuntu 12.04 32-bit, using my old Asus eeepc. I plugged it into my new laptop and booted. After Ubuntu loaded I plugged my USB modem Huawei E1552. I expected a window to pop-up asking me to enter PIN and then allowing me to setup internet connection. But it didn't. No pop-up window, nothing about mobile broadband in network-manager applet. I opened terminal and entered
lsusb:
 Bus 003:ID 12d1:1446 Huawei E1552/E1800 (HSPA modem)
Yes! The dongle IS recognized. But obviously the modem-manager is not loaded. I tried another USB dongle Huawei E367. The same thing. Then I  moved to my old lappy Asus: inserted the same usb-drive (ubuntu 12.04 - 32 bit). Started it, then I inserted the modem. It works! The other Huawei works too. I tried other distributions (Kubuntu 12.04,Mint 13, Ubuntu 12.04 -64 bit,Kubuntu 12.10). I tried Sakis3g. It shows me: unable to setup device. Nothing works.
On Windows 7 both Huawei work fine. On my old comp work too (same live flash-pen). This models are supported in linux, I have been using them for years.
    I have no wired or wireless internet and I rely on mobile broadband only.
P.S. I'm just an average user and I expect things to just work. I can do some things in terminal but I'm not deep in this stuff.
  Any ideas?
 By the way it shows me restricted driver available (Broadcom), but without internet I can't install it. But is it important for the mobile broadband?

---

### Post by ilia_avramov on 2012-11-26
Thank you for the many replies. Sakis3g did the trick but after I disabled PIN verification. I couldn't connect to internet during instalation but after I inslalled Ubuntu 12.04 64bit It connected successfully. Now sometimes it connects automaticaly, sometimes it can't and then I start Sakis3g which works better than the default modem-manager.

---

