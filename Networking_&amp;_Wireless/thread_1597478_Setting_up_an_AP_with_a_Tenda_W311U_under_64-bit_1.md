---
title: "Setting up an AP with a Tenda W311U under 64-bit 10.04"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Technous285 on 2010-10-15
I am currently trying to set up my Tenda W311U USB WiFi Dongle under Ubuntu 10.04 (64-bit) on either my Latitude D620 laptop or Optiplex 745 desktop to act as an access point for me to use to connect my DS Lite & DSi (and let ONLY those two devices connect to it) to my network.

I have previously managed to do such under XP Pro by using the Windows drivers and control program along with bridging the dongle with the ethernet, but am unable to use that same method withing 10.04.

For those interested - I have no idea what drivers are running the dongle, only that it seems to let me TRY and access any wifi APs nearby, but won't let me set it up to act as an AP itself.

Edit @ ~5:50oam AEDT;
I've been reading another thread which deals with the RALink 2800/2870 drivers (for the chipset in dongles like the Tenda W311U) and how to prevent the 2800 drivers from conflicting with the 2870 and followed the instructions so only the 2870 drivers are left.
I've downloaded and unpacked the files for the 3070 drivers, but haven't tried installing them yet.

---

### Post by Oiorpata on 2010-11-08
I never did manage to get the Tenda W3111U working with anything better than WEP on 64bit ubuntu 10.04, it would time out trying to connect using WPA. 
The good news is that after upgrading to version 10.10 the problem has vanished.

---

