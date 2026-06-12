---
title: "WiFi: Ubuntu 12.10 on Lenovo B590 with Broadcom BCM4313 Wireless LAN Controller"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Steven McTowelie on 2013-04-11
I thought it might be useful for other Ubuntu 12.10 users that have a Lenovo B590 Notebook with a Broadcom 4313 Wireless LAN Controller. After I did this my WiFi worked:

[B]sudo apt-get install --reinstall linux-headers-generic linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl[/B]

(Source: [http://askubuntu.com/questions/223900/why-has-wireless-disappeared-after-my-12-10-upgrade](http://askubuntu.com/questions/223900/why-has-wireless-disappeared-after-my-12-10-upgrade))

---

### Post by joachim_altmann on 2014-01-19
Worked for Ubuntu 12.04, 64bit, on a Lenovo B590 with BCM43142 Wireless LAN Controller as well. Thanks, Steven.

---

### Post by Nik_Nenkov on 2015-01-16
Thank You Sir ! This was very helpful ! I used only the second line: **udo apt-get install --reinstall bcmwl-kernel-source **and it worked perfectly ! Thanks !

---

### Post by slickymaster on 2015-01-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Rob Sayer on 2015-01-18
The most useful thing for ubuntu 12.10 users would be to reinstall using 14.04.  12.10 reached end of life last May.  It's not secure anymore.

---

