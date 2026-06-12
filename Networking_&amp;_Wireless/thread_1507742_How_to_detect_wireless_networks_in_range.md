---
title: "How to detect wireless networks in range?"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by Wormy1969 on 2010-06-12
My unix/linux days are long behind me but I find myself fixing my roomates laptop. He recently stopped auto connecting to our wireless network. My desktop is still fine so that should not be the problem. I have tried to follow some of the trouble shooting instructions to no success. What I have learned.
 
Ubuntu 9.04
 
Network controller: Broadcom Corporation BCM4311 802.11b/g
 
eth1 - IEEE 802.11 Nickname:""
Access Point: Not-Associated
 
Device eth1
Type: 802.11 WiFi
Driver: wl
State: disconnected
 
 
How do I see a list of wireless networks in range to connect to?
The NetworkManager (left click) "Wireless Networks" option is grey.
The NetworkManager (right click) "Enable Networking" and "Enable Wireless" options are both checked.
 
Any help would be greatly appreciated.

---

### Post by varspare on 2010-06-12
Hi Wormy1969,

You can usually get the system to scan by disabling and reenabling the wireless network. 
Alternatively you could try running;
#sudo iwlist scanning
(you may need to sudo to find everything)
this will try each interface on the machine and attempt to scan for networks.

Let us know what you find.

Varspare

If the scan fails you might need the driver from broadcom: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Wormy1969 on 2010-06-12
Thanks for the advice Varspare, but it turns out my roomate is an idiot and I am blind.  He had flicked the wireless off on his laptop.

---

### Post by varspare on 2010-06-13
> **Wormy1969 said:**
> Thanks for the advice Varspare, but it turns out my roomate is an idiot and I am blind.  He had flicked the wireless off on his laptop.

No worries, I think we've all been there at some point.

---

