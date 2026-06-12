---
title: "Slow filesharing over WiFi"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by Sinopa on 2011-02-15
Most of my computers run Ubuntu 10.10 except 2 that has Windows XP.  
 When I share files between the Windows computers, the files are transferred really fast, but when I try to transfer files to and from a computer with Ubuntu I only get 1 MB/s file transfer.
 

 I've been looking for solutions all over, but haven't found any.  
 

Does anyone know how I can solve this problem?

---

### Post by mr_luksom on 2011-02-16
Unfortunately that is the nature of wireless. I had 802.11n, and never got better than that. 

If you need faster, you will need wired lan or 'Power over Ethernet'

---

### Post by Grenage on 2011-02-16
> **Sinopa said:**
> Most of my computers run Ubuntu 10.10 except 2 that has Windows XP.  
 When I share files between the Windows computers, the files are transferred really fast, but when I try to transfer files to and from a computer with Ubuntu I only get 1 MB/s file transfer.
 

 I've been looking for solutions all over, but haven't found any.  
 

Does anyone know how I can solve this problem?

This sounds like a driver issue, since the connection is decent between Windows XP machines.  If alternative drivers are available, it might be worth a shot.

---

### Post by Sinopa on 2011-02-17
Grenage to the rescue :D

I installed ndiswrapper and installed the windows driver, but no change.

---

### Post by Grenage on 2011-02-17
Ahoy again!

What adapters are you using on the Linux machine?

---

### Post by tgalati4 on 2011-02-17
Do you have any wireless "b" devices like an old printer?  Any "b" devices will force your entire network to "b" speeds.  It could also be wireless interference with the neighbors.  Try scanning your area with wifi radar.  I presume the Windows XP machines are wired together or are they wireless as well?

---

