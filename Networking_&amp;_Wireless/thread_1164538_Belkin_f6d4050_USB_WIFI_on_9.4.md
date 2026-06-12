---
title: "Belkin f6d4050 USB WIFI on 9.4"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Adam25 on 2009-05-19
From what ive read the newest release is supposed to support the chipset of the usb wifi adapter. So i upgraded from 8.10 to 9.4 today. It uses Ralink 2870, lsusb shows "bus 001 ID 050d:935a Belkin Components". With the adapter on my notebook it lights up thats it. I can figure out how i get ubuntu to find and add the drivers the new version is supposed to have. Any help?

---

### Post by Adam25 on 2009-05-20
Can someone help me out plz? ndiswrapper shows the driver installed.. But i still cant figure out what to do to get it to work.

---

### Post by SeaJayEmm on 2009-12-27
You need the rt2870.inf and the rt2870.sys file from the winx64 driver. You will be able to find these files on the Windows driver cd that came with the usb adapter. If not I can email them to you. Then install with ndisgtk, reboot your machine and you will have wireless access.

---

### Post by genfly on 2010-01-28
Hey, do you still have the rt2870.inf and the rt2870.sys for Belkin f6d4050 USB WIFI on Ubuntu 9.4? It would be amazing if you could email me them. Thanks every so much in advance. My email is [email]ichimato@gmail.com[/email]

---

