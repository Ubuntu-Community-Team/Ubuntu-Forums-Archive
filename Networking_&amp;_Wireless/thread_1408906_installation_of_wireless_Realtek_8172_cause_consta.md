---
title: "installation of wireless Realtek 8172 cause constant reboot"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by bek on 2010-02-17
Pls, need help, I could install wireless driver  as it was said in [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172), but I am facing another problem. it is new Toshiba Satellite P505, so i had no problems with installation of 9.10, all necessary drivers, but what happened since i have installed realtek, my laptop started to reboot itself, so I thought it was overheating problem, trying to find some solutions, but later on, right now, I am working without wifi, it is work smooth, no problems, and I do the same tasks I did with wifi. so it seems it is either problems with driver or kernel? any comments, how to make wifi work, and not cause problems?

---

### Post by bek on 2010-02-17
so far, I had tried different ways to fix it, but still the issue is unclear. 
1- problem with fan control and overheating, I even tried to edit grub by adding *acpi_osi*="*Linux*" which did not work.
2-  problem with conflicting atheros **AR8132** lan and realtek wifi 8172 drivers, tried to blacklist atheros 
3- tried to use different wifi connections from WEP to WPA2, as it was suggested

As for the 2 problem, the laptop run longer, and I was almost happy that it fixed the problem, but it started to reboot again.

Right now working just with atheros, disable wifi, and everything is fine.

So any problem solutions?

---

