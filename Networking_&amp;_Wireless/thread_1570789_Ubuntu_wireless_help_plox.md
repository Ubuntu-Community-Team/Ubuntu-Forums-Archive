---
title: "Ubuntu wireless help plox"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by HHAbendroth93 on 2010-09-08
Hi new to ubuntu and i just recently installed ubuntu server x86 10.04.1 edition and for the life of me i can't get the wireless card working. Its an atheros ar928x wireless card and i don't know what to do. I don't have any experience in linux and any help would be appreciated. thanks

---

### Post by HHAbendroth93 on 2010-09-09
when i try to connect ubuntu server 10.04.1 to my wireless internet i get the error ( no private ioctls ). This only happen when i try to use several commands to setup the internet. I have a wpa1 connection. Any help would be appreciated.

---

### Post by HHAbendroth93 on 2010-09-09
I'm very new to linux and i just installed ubuntu server on my laptop. I've been looking for days on how to solve my problem but nothing helps.
 It's using a Atheros ar928x wireless card.
 
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "box10"
sudo iwpriv wlan0 set AuthMode=WPAPSK
no private ioctls
sudo iwpriv wlan0 set EncrypType=TKIP
no private ioctls
sudo iwpriv wlan0 set WPAPSK="*******"
no private ioctls
sudo dhclient wlan0
 
 
I can't connect to my wifi and i don't know what to do. It's the wpa1 security. Any help please

---

### Post by overdrank on 2010-09-09
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by BkkBonanza on 2010-09-09
I have an AR9281 and it works well with default drivers in Ubuntu.
For WPA you need to use wpa_supplicant.
This tutorial is old now but may help you get there.
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

