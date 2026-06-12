---
title: "aircrack help"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by wkdw1ll1ams on 2010-11-20
first i would like to say im sorry if this is the wrong section.
im new to ubuntu and trying to learn how everything works. any way on to my problem.

when i type aireplay-ng -1 0 -a 00:26:44:66:2D:C5 -h 00:11:22:33:44:55 wlan0 in terminal i get: 
no such bssid available
please specify an -e (ESSID)
i tried putting the essid but i get the same error.

i did a test to see if my driver supports injection. heres my result:

aireplay-ng --test wlan0
12:12:19  Trying broadcast probe requests...
12:12:21  No Answer...
12:12:21  Found 6 APs

12:12:21  Trying directed probe requests...

12:12:28  00:26:44:66:2D:C5 - channel: 11 - 'PlusnetWireless'
12:12:34   0/30:   0%

help would be great.

edit: i havnt patched my driver. i checked on the aircrack compatible  driver site and my driver is compatible but it says patching the driver  is optional. i dont no how to patch the driver.

---

