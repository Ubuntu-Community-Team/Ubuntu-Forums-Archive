---
title: "Wi-Fi config info"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by coldraven on 2010-08-22
Hi all, can someone tell me what this output means?
I always have a Red exclamation mark on the task-bar icon but it always connects promptly and stays connected.
This is using my home router, I have not tried it elsewhere.

```
jamie@happy32:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

```Is it possible to  find out more information about my connection.?

---

### Post by SonnyKing on 2010-08-24
You can use iw, iw list, iw dev wlan0 link..etc

---

### Post by Iowan on 2010-08-24
Unless your interface is configured via Network Manager, it (Network Manager) may complain.

---

