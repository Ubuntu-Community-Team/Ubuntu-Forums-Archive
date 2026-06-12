---
title: "Problems with Belkin F5D7051 and Lucid Lynx"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Mollusssc on 2010-06-08
I have been looking all over the internet for a solution for this to no avail.

I have a USB Belkin F5D7051 WLAN dongle and Ubuntu 10.04
I have installed the ndiswrapper on the disk of 10.04 and used the bcmrndis.inf file found on the disk of my Belkin dongle. I manually copied the usb8023k.sys and rndismpk.sys files to etc/ndiswrapper/bcmrndis.

Now according to ndiswrapper there are no problems, however, when i try to connect to a network using the network manager, it hasnt enabled any wireless settings so i cannot search for networks "/

Any help would be appreciated :D

Many thanks

---

### Post by Mollusssc on 2010-06-08
Bump

---

### Post by Mollusssc on 2010-06-09
For anyone interested, i have it working now.
Although it isnt brilliant at all.
Im getting 5mbps (Y) Nice one.
Considering just buying a new one.
Anyone got any suggestions?
54mbps (+) If poss for about £20?

---

### Post by AstarothSquirrel on 2011-01-02
How did you get from not having network capability to getting connected?  I have the same problem.  I've installed the Ndis driver.  Shows up fine in lsusb.  Shows up fine in the Ndis gui.  Just isn't showing up in network-manager.  I've added 
BUS==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;7051&#8221;, SYSFS{idVendor}==&#8221;050d&#8221;, \ PROGRAM=&#8221;/bin/sh -c &#8216;echo 1 > /sys/%p/device/bConfigurationValue&#8217;&#8220;
to /etc/udev/rules.d/z25_local_rules

Still I have no Wlan0 and it won't scan for wireless networks.  This all started because I moved my desktop to a different room to my router and now it picks up all my neighbours routers but not my own (despite my win7 laptop picking up my router from further away)  I figured that it must be a signal strength thing in ubuntu (from other forum posts) and thus I started on this sorry path of misery.

If you can remember what you did to get your wireless connection, please let me know.
Many thanks

(I really do not want to sacrifice stability and reliability by going back to MS XP just to get my wireless working.  Yes, the exact same machine in the exact same location running XP picks up my router fine.)

---

