---
title: "gprs and ubuntu 8.04"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by avinash3375 on 2009-07-23
how to connect net via gprs(nokia) in ubuntu 8.04:confused:

---

### Post by arunkumar413 on 2009-08-05
ubuntu 8.04 has program called "wvddial".follow the below steps to connect:
1)connect your phone to the pc using the data cable.
2)open the terminal and type **gksudo wvdialconf**.
3)the modem configuration will be written to the /etc/wvdial.conf
4)open the wvdial.conf file and edit the file by changing the dialing number and save the file.
5)Now type wvdial in the terminal.This will connect to net.
6)open the browser and browse the net.

---

