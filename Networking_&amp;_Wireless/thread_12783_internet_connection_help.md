---
title: "internet connection help"
date: 2005-01-26
forum: Networking &amp; Wireless
---

### Post by wainop on 2005-01-26
I am booting ubuntu from the live cd. I can't figure out how to connect to the 
internet. I have a dsl conection.

---

### Post by hardcandy on 2005-01-26
Open a console, type "sudo ifconfig eth0 up" and then "sudo ifconfig". See if shows two interfaces, one will be localhost and the other should show a IP address. What brand and type (wireless, usb, NIC?) if it does not show.

---

