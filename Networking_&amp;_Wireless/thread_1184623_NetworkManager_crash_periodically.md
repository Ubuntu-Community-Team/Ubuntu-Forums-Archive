---
title: "NetworkManager crash periodically"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Vecheslav on 2009-06-11
Hello!  
 I recently installed Ubuntu 9.04 on my EEE PC 1000.  
 To connect to the internet I use Anydata 310a CDMA modem.  
 Ubuntu recognizes it and works fine with it.  
 But I have the occasional problem with the sustainability of the NetworkManager  
 I get a message that he is not running. I looked through the file /var/log/messages and found the following message  
 slava @ slava-laptop: /var/log$ cat messages | grep segfault  

 Jun 6 20:34:56 slava-laptop kernel: [1299.472271] NetworkManager [2926]: segfault at 20 ip 0809c3af sp bffb4a20 error 4 in NetworkManager [8048000 +67000] 

 Jun 10 10:52:08 slava-laptop kernel: [58.098535] NetworkManager [2906]: segfault at 0 ip b7b1307a sp bff1e3cc error 4 in libc-2.9.so [b7a9c000 +15 c000] 

 Jun 11 18:03:05 slava-laptop kernel: [551.539630] NetworkManager [2894]: segfault at 20 ip 0809c3af sp bfa13690 error 4 in NetworkManager [8048000 +67000] 

 Jun 11 18:19:07 slava-laptop kernel: [1513.448685] NetworkManager [4544]: segfault at 20 ip 0809c3af sp bfab2c40 error 4 in NetworkManager [8048000 +67000] 

 slava @ slava-laptop: / var / log $  

 I installed the latest updates, but the problem is constantly repeated.  
 Are there any ideas how to fix? Thanks in advance.

---

### Post by Vecheslav on 2009-06-27
[LEFT]Hello! 
 I switched my modem to the EVDO only mode 
 Posde this bug in NetworkManager stopped[/LEFT]

---

