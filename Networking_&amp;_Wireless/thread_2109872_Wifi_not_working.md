---
title: "Wifi not working"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by doogeo on 2013-01-28
Hi, so I am new to ubuntu and getting rather frustrated and was wondering if anyone could help. I downloaded an iso image on to a memory stick and booted an old pc i have from it to try out ubuntu and decided i liked it. While i was booted from my memory stick i was able to access the internet absolutely fine.

I then went on to install ubuntu and restarted my pc. However now it wont connect to the internet. I can view available networks and try connecting, but it just keeps saying connecting for ages and then disconnects. However after logging on to my router (virgin super hub) on my laptop it says that my desktop is connected. 

I try loading webpages to no avail. Also it would connect to bt wifi so it will connect to the internet just not my internet

Any help on anything i can try or do to find out the issue would be greatly appreciated

---

### Post by Crafty Kisses on 2013-01-28
Can I get results of 
```
lsusb
lspci
```

---

### Post by vinayuga on 2013-01-28
I am also facing similar trouble. (The ubuntu OS is installed on qemu emulator. ) . Could you give some direction?

$lsusb
unable to initialize libusb:-99
$lspci
00:19.0 Ethernet controller: Intel Corporation 82540EM Gigabit Network Connection (rev 03)
$iwconfig
lo   no wireless extensions
eth0 no wireless extensions

---

### Post by Crafty Kisses on 2013-01-30
> **vinayuga said:**
> I am also facing similar trouble. (The ubuntu OS is installed on qemu emulator. ) . Could you give some direction?

$lsusb
unable to initialize libusb:-99
$lspci
00:19.0 Ethernet controller: Intel Corporation 82540EM Gigabit Network Connection (rev 03)
$iwconfig
lo   no wireless extensions
eth0 no wireless extensions

Have you read any of the QEMU documentation?

---

