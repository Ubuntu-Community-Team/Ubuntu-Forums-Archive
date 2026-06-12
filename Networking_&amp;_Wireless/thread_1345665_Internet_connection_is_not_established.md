---
title: "Internet connection is not established"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by madhavan00 on 2009-12-04
i am using ubuntu and windows XP in my PC.
for the past few days im not able get my internet connection in ubuntu but im getting my internet connction in XP.
while in ubuntu its shows that "DEVICE IS NOT MANAGED"........
im not able to find any solution for this problem....................
now im using internet in XP which is not fine when compared to ubuntu............
PLEASE can any one able to solve my problem i'll be thankful to u.........


I AM USING UBUNTU 8 and INTERNET IS BROADBAND

---

### Post by Iowan on 2009-12-04
There are two Ubuntu 8's - 8.04 (Hardy) and 8.10 (Intrepid). Open a terminal and check:```
cat /etc/network/interfaces
``` It should have only a couple of lines configuring "lo". If there's a definition for another interface (eth0), Network Manager won't touch it - thus the "unmanaged" message. You should be able to configure your interface either way (Network Manager is preferred).

---

### Post by madhavan00 on 2009-12-04
> **Iowan said:**
> There are two Ubuntu 8's - 8.04 (Hardy) and 8.10 (Intrepid). Open a terminal and check:```
ifconfig -a
``` It shold have only a couple of lines configuring "lo". If there's a definition for another interface (eth0), Network Manager won't touch it - thus the "unmanaged" message. You should be able to configure your interface either way (Network Manager is preferred).

thanx a lot........
but how to configure by using network manager. im new to ubuntu so pls help me.............

---

### Post by Iowan on 2009-12-04
Wow! I messed that up... */etc/network/interfaces* is the file that should have only the definition for "lo". If it has definitions for eth0, they can be commented out.  You'll need to edit the file via ```
sudo nano /etc/network/interfaces
``` or ```
gksudo gedit /etc/network/interfaces
``` - depending on which editor you prefer. "Comment out" the line by inserting a # at the beginning of the line.

---

