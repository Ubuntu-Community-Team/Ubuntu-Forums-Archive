---
title: "Slow local network"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by Harry.k on 2012-12-25
I'm not sure this is a problem with Ubuntu, but i don't want to leave any stone unturned.
Here is my setup : 


```
               (d-link dsl-2730u)
                       |
                       |
_______________________|____________________________
---|----------------|---------|--------------------|
WiFi(a/b/g)/LAN    LAN       WiFi(a/b/g/n)     Mostly WiFi
   |                |         |                    |
(Asus eeepc)     (Old pc)   (Galaxy S3)       (Other stuff)
```

All connections are through router and all computers Ubuntu 12.04 or newer. No additional drivers were needed.

SFTP file transfer speeds across the local network is as follows:

eeepc<--LAN-->old pc : 4 MBps
eeepc<--WiFi--LAN-->old pc : 2.2 MBps
eeepc<--WiFi-->S3 : 1.5MBps
S3<--WiFi--LAN-->old pc : 1.5 MBps

Can anyone explain the slow speeds? the router is gigabit ethernet and n150. Eeepc and old pc are 100Mbit ethernet.

---

### Post by chadk5utc on 2012-12-25
What type internet connection do you have DSL? just guessing 
whats the speed your ISP stated??
Remember Wifi connections are shared type connections meaning that one connected device gets full speed 4 connected devices get 1/4 speed Each. The device may show its connected and full speed but through put will not be the full speed. There are also a number of things that can affect Wifi performance, walls, distance, cordless phones, microwave ovens. With wifi your dealing with 2.4Ghz radio frequencies the antennas are less than 1.5" and most "OTS" Off The Shelf gear is not very high output usually .20-.30milliwatts good for the average home but not distance, walls, file cabinets.... Try to relocate your wireless and see if it helps at all...Final note wired connections will always be faster

---

### Post by Harry.k on 2012-12-25
The internet is fine. My problem is SFTP transfer across the devices connected to my router.

---

### Post by chadk5utc on 2012-12-25
I just tested my home network with a 150mbit file and then tested my office vpn. The home network runs @560-750kb/s the vpn a little slower.

---

### Post by Harry.k on 2012-12-26
bump

---

### Post by Harry.k on 2012-12-28
bump

---

### Post by BertN45 on 2012-12-28
> **Harry.k said:**
> 
SFTP file transfer speeds across the local network is as follows:

eeepc<--LAN-->old pc : 4 MBps
eeepc<--WiFi--LAN-->old pc : 2.2 MBps
eeepc<--WiFi-->S3 : 1.5MBps
S3<--WiFi--LAN-->old pc : 1.5 MBps

Can anyone explain the slow speeds? the router is gigabit ethernet and n150. Eeepc and old pc are 100Mbit ethernet.
At the LAN of 100 Mbits/s you will not get more then 10 MByte/s based on pure I/O throughput because of protocol and headers overhead. If you start adding the interrupt processing times on both sides and inside the router the 4 MByte/s does not seem unreasonable. For the wifi 40% of 5.4 MByte/s gives the 2.2 MByte/s. So quite normal. Your S3 Phone? is slower, probably because the wifi HW and driver are less efficient or maybe the SD-Card is limiting the speed. More cores do not really help for this type of processing, higher clock speed would help.

---

### Post by Harry.k on 2012-12-28
Its already overclocked by around 25 percent. The memory is an emulated sdcard in the internal storage that supports full hd recording. The laptop android the phone support wifi-n. I really cant figure out what the bottleneck is. Thanks for explaining the wired speeds.

---

### Post by Harry.k on 2012-12-29
Bump

---

### Post by Harry.k on 2013-01-01
Bump

---

