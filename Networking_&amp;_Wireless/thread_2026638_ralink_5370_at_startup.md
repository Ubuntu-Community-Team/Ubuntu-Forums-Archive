---
title: "ralink 5370 at startup"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by amoateng on 2012-07-15
I bought these wireless usb adapters and after several days managed to install the driver on ubuntu 12.04 with this method:

sudo su
make clean
make
make install
modprobe rt5370sta
exit

it worked and the desktop computer could connect to wireless routers. i thought it was all good till i restarted the computer. The driver installation procedure has to be done every time the computer boots. How can i make the computer "remember" the wireless usb adapter?

---

### Post by chili555 on 2012-07-15
Please do:```
sudo su
echo rt5370sta >> /etc/modules
exit
```Reboot and let us have your report.

---

### Post by amoateng on 2012-07-15
holy **** dude it works!!


thanks man!

---

### Post by chili555 on 2012-07-15
How about using thread tools at the top and mark Solved? Glad it's working.

---

