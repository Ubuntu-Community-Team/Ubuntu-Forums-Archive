---
title: "Help connecting with Linksys WMP54GS network adapter"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by ieee488 on 2008-12-21
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by bruce64 on 2008-12-21
Heres my two cents.  If you've only used this for four days, I would be tempted to suggest reinstalling.  I have a Dell Inspiron6000 and the ndiswrapper issue was a pain in the neck.  Bottom line, last two distros Hardy, Intrepid both found the drivers automatically.  The best way to get things up and running.  Reinstall.  Update manager and update all packages.  Reboot.  Go to System -> Administration -> Hardware Drivers.  You should see your wireless driver, you may be prompted to load the firmware after you load the driver, reboot your machine.  The wireless light should be on upon start up. If not you might need a second reboot but it will work out of the box.  Ubuntu was a godsend when detecting my card - Broadcom Airforce 1.

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by bruce64 on 2008-12-21
You will be prompted to overwrite the ubuntu partition.  Choose yes and take it from there.

---

### Post by ieee488 on 2008-12-21
The Linksys WMP54GS reportedly has the Broadcom 3406 chipset which reportedly is detected by default in Ubuntu 8.10.

It is simplifying things too much to see that all wireless problems are going to disappear by using 8.04 or 8.10. They don't. I have a Dell D400, and in 8.04, the Dell Truemobile miniPC which has Broadcom 3406 chipset had issues even when using ndiswrapper.

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by saultpastor on 2008-12-21
open a terminal type

lspci

look for your network controller in the list.

If it is not there type

dmesg

look for something pertaining to wlan

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by saultpastor on 2008-12-21
ok type

lsmod

in the terminal and post the results here

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by Ayuthia on 2008-12-21
Since the hardware is not present, it means that the ndiswrapper does not like the driver that you are using.  You might try the driver in this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by mp5shooter on 2008-12-21
-removed-

---

### Post by mp5shooter on 2008-12-22
-removed-

---

### Post by mp5shooter on 2008-12-22
-removed-

---

### Post by saultpastor on 2008-12-22
I have personally never gotten the Ubuntu network manager to work with my wireless (laptop)

I use wicd with great success, I have no idea why Ubuntu uses network manager.  Search for wicd there is a .deb for it as well as a python script for the taskbar applet.

---

