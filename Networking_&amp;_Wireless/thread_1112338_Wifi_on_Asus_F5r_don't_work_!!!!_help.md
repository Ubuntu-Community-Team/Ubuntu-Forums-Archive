---
title: "Wifi on Asus F5r don't work !!!! help"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by orgrud on 2009-03-31
i have a problem with my wireless card, and i can't get to work with ubuntu
i run ubuntu 8.10, my laptop is a Asus F5R the network controller is a  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

can anybody help me?

---

### Post by albertu on 2009-04-05
I have the same problem,too

---

### Post by orgrud on 2009-04-06
i have found a solution . to activate the network card i have to put the laptop in suspend or hibernate mode when i start the laptop from one of thes modes the card works.

then again this i very boring to do every time i start my computer. do anybody have a solution?

---

### Post by stenlikobra1 on 2009-07-20
Hi people, I've got a solution of this problem. :D:D:D :) Finally it works... :))

Just open Terminal and edit a file: " gksudo gedit /etc/rc.local "
Befor the line exit 0 paste: " echo 1 | tee /sys/devices/platform/asus-laptop/wlan " without sudo, because it is runing as superuser file.
Then just save this file and close and restart comp, and it should work. :)
That's all... :D

---

