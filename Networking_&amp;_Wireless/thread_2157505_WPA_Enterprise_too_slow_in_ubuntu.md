---
title: "WPA Enterprise too slow in ubuntu"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by navid65 on 2013-06-25
when I want to connect to wireless in my university which is Wpa2 Enterprise, after 2 or 3 tries I finally connect but the speed is so slow. I tried kubuntu and it was fine and I got good performance. So I think the problem is with Gnome NetworkManager. Does anyone know what the problem is? I really like to use ubuntu instead of kubuntu.

Thanks.

---

### Post by gordintoronto on 2013-06-25
This might be the problem: Sometimes the problem in 'campus' type networks is that they have multiple access points sharing the same ESSID. That can make the wireless device go crazy trying to roam to the nearest / strongest access point. Run this command: sudo iwlist scan
Add the MAC-address of the nearest access point into the field "BSSID" in the network-manager applet. (You'll need to change it if you move to a different location.)

---

