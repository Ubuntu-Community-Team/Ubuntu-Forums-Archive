---
title: "WPA/TKIP working but not WPA2/AES"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by craber on 2010-10-13
First, I've dinked around with Linux b4 but never really considered it for an everyday desktop machine. After installing the ubuntu 10 release I have to say I am really impressed. This is going to be the kids homework machine! :guitar:

I had one challenge during the installation and that was getting wireless networking going. I set up Win XP first (to get the ndis driver and validate connectivity).

After installing ubuntu I could not get the adapter (Netgear N300/USB) to connect to our router (D-Link DIR-825) using WPA2 and AES. Finally I got it to work after setting the router to only TKIP encryption. This works ok but causes the adapter to operate at a lower connection speed :mad:

I tried the wcid alternative network manager but that did not help. Any pointers much appreciated!!!

---

### Post by craber on 2010-10-14
Let me ask it this way, does anyone have WPA2/AES working with ndiswrapper?

Was any special setup required?

TIA.

---

### Post by switcha on 2010-11-27
Hi,

I have the same issue except I am using WPA-PSK. WPA-PSK works perfectly fine, however, when I change my netgear router settings to WPA2-PSK or WPA-PSK + WPA2-PSK, ubuntu 10.04 fails to connect.

I have found this article located [here]("http://ubuntuforums.org/showthread.php?t=202834") but haven't had the opportunity to fully investigate it.

If you're keen it might be worth a read.

Anybody with any other suggestions for the both of us would be appreciated,

Regards,

~Switcha~

---

### Post by cybergnome on 2010-11-28
The obvious question is what does your wireless adapter support?  Both devices must support the configured scheme for it to work.  Also, the router's configuration may be limited if there are both WPA and WPA2 stations on the network.

---

### Post by astabeno on 2011-12-03
I am having the same problem with 11.10.  Both my adapter and my router support WPA2-AES but only WPA2-TKIP will work, even though my router says Wireless N Networks don't official support TKIP encryption.

---

