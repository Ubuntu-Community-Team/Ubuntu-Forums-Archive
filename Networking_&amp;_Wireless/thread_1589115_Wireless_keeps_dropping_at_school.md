---
title: "Wireless keeps dropping at school"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Fittersman on 2010-10-05
I'm running ubuntu 10.04 on my laptop with broadcom BCM4322 wireless card. Other specs are:
    * Intel T6500
    * Intel GMA 4500MHD
    * 60GB OCZ Summit SSD
    * Broadcom BCM4322 Wireless

Basically what keeps happening is my wireless will stop working, then network manager will notify me that I have lost signal. It will then try and reconnect, but it never seems to be successful. The only way I can get the wireless to work again is if I disable wireless then re-enable wireless (or do a complete system restart). 

However, it does not seem to have this problem at home. The only difference I can think of from home and school is either encryption types (the university uses WEP, I use WPA) or the fact that at home there is only one access point and at university there are multiple access points all with the same SSID.

Anyone have any idea how to make my laptop stop dropping connection all the time? I don't recall ever having this problem before I started using ubuntu 10.04 (I think I was using Debian last year at university).

---

### Post by P4man on 2010-10-06
Are you using restricted drivers for that card? If not, have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

If neither the kernel nor the restricted driver work properly, you can always use ndiswrapper to load the windows driver.

---

