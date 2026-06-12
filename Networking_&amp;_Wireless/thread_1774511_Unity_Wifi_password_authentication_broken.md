---
title: "Unity Wifi password authentication broken"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by cjpetrie on 2011-06-03
Sony Vaio X upgraded to 11.04 with 2.6.38-8-generic i686 which improved some features but which introduced a serious WiFi problem: while unsecured WiFi works well, connecting via WPA & WPA Pesonal password fails consistently despite reboots of everything and renaming of SSID. Another laptop running 10 still works fine. One hint: upon upgrading, there was the warning that the laptop hardware did not support Unity and I always get the classic Gnome display.
Atheros AR9285 Wireless Network Adapter
Qualcom Sony Gobi 2000 Wireless Modem
ifconfig shows no packets with wlan0 or any connectivity.
iwconfig shows correct SSID and other info.
dmsg shows "wlan0: direct probe to f8:7b:7a:2b:a7:d1 timed out"
Restarting the network has no effect but there is a message that 
"Running /etc/init.d/networking restart is dprecated because it may not enable again some interaces"
I don't find this same problem in the forum so perhaps it is some configuration error on my part. Please comment if you have any clues.

---

### Post by cjpetrie on 2011-06-04
Someone else reports the "hardware does not support unity" and wifi problem with a different ultraportable: [http://ubuntuforums.org/showthread.php?t=1764218&highlight=unity+wifi+problem](http://ubuntuforums.org/showthread.php?t=1764218&highlight=unity+wifi+problem)

---

### Post by cjpetrie on 2011-06-04
Here is another report of 11.04 allowing only unsecured connections: [http://ubuntuforums.org/showthread.php?p=10898347](http://ubuntuforums.org/showthread.php?p=10898347)

---

### Post by cjpetrie on 2011-06-06
My bad: the problem is not security. But 11.04 does not work with a DROID hotspot even if unsecured.

---

