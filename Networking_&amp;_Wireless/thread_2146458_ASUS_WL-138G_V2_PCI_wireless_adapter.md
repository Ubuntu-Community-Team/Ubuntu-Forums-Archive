---
title: "ASUS WL-138G V2 PCI wireless adapter"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by adolfson on 2013-05-18
Hello,my problem is I downloaded ubuntu 13.04 and installed it on my pc but being very new to linux i can not figure out how to get my internet connection working. 
"Asus WL 138G v2" is the name of my adapter. Is there anybody here who could help me with this one?

---

### Post by Geoff918 on 2013-05-18
One thing that will be helpful to really drill down would be that you inventory your hardware:

You can issue the following command:

sudo lshw -html > hardware.html

which will create a HTML file with the contents. Alternately, you can issue:

sudo lshw > hardware.txt

to get a non-formatted version.

From there we can grep the output and find the exact specs on the wireless card.

---

### Post by adolfson on 2013-05-18
Okay i got html file this is the source of that file -> [http://snipt.org/AaNb8](http://snipt.org/AaNb8)

---

### Post by adolfson on 2013-05-18
Sorry that snipt.org didnt work quiet well. Here is better source [http://pastebin.com/KpYv2k07](http://pastebin.com/KpYv2k07)

---

### Post by praseodym on 2013-05-18
Hi,

for your Broadcom 4318 device you only need to install the package "linux-firmware-nonfree" via cable connection with the software-center.

---

