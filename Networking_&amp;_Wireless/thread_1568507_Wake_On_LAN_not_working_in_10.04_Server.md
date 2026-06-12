---
title: "Wake On LAN not working in 10.04 Server"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by Razican on 2010-09-05
Hello, I have Ubuntu 10.04 Server in a machine with an ethernet card wich has "Supports Wake-on: pumbg" and "Wake-on: g". In the BIOS I have "Wake On LAN" Enabled, "Wake on S5" Enabled and "ACPI suspend type" S3.

I do sudo shutdown -h now and it halts the system. And then, I try to power up from a laptop with Ubuntu 10.04 desktop with wakeonlan: "wakeonlan -i 192.168.1.100 00:27:19:B5:XX:XX" (with upper case letters), but nothing occurs. It does not power on the system.

I have opened the port 9 in the router to power the computer from everywhere in the net, but I have only tried to do it in LAN, and it does not work.

---

