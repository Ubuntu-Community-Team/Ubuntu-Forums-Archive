---
title: "Belkin Enhanced Wireless USB Network Adapter Model # F6D4050 v2"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by davidtolo on 2010-02-03
Hello,

I have a Belkin Enhanced Wireless USB Network Adapter Model # F6D4050 v2.

The drivers are for windows but the windows wireless drivers app doesnt work.  I see a tutorial for a linksys that appears to have the same chipset, but I am not sure if any of the steps need to be modified, also my kernel is a bit different.

Here is my kernel:

 Ubuntu 9.10 - the Karmic Koala
it is 64 bit (ubuntu studio)
 uname -a
Linux ubuntuStudio 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux

Here is the results of lsusb:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anyone help me?  I am seeting this up for someone who is less fortunate and help would be much appreciated.

Thank You,
David

---

### Post by SeaJayEmm on 2010-02-14
Well the first thing you will need to do is plug your computer into your wireless router via an ethernet cable. Update your system by opening a terminal and typing "sudo apt-get update". After update is complete in terminal type "sudo apt-get install ndisgtk". Create a folder in your home directory named Wireless and copy over the XP_64 rt2870.inf and the rt2870.sys to the newly created folder. Open ndisgtk by typing "ndisgtk" in terminal. From there click install driver. navigate to the rt2870.inf file and click install. Reboot your computer and BAM you have wireless.

---

