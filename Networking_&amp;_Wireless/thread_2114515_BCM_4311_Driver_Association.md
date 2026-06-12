---
title: "BCM 4311 Driver Association"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by accentbg on 2013-02-10
Well, I went with this Ubunutu instead of windows. I did a new 12.10 installation onto a Dell Latitude d620. All worked fine except for wireless. I found these directions on the site. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
In going through this I got stopped at section 3.3.2.1. where I was to check to see if driver was installed correctly. It appears the driver is associated with another device then what it should be yet there is no directions on how to fix this. 
 
I found that I had:
0c:00.0 Network Controller: Broadcom Corp BCM4311 802.11a/b/g (rev 01) 
 
I ran lspci -n and found: 
0c.00.00 0280: 14e4:4312 (rev 01)
 
then I ran ndiswrapper -l and found:
b57nd60x : driver installed
device (14E4: 1600) present (alternate driver: tg3)
 
So it appears my driver is not associated correctly for me to move forward with the fixes. 
 
Can anyone offer any advice?:(

---

### Post by kc1di on 2013-02-10
Why not just got to system setting and additional drivers and install the driver for your card there.  you may have to undo what you've already do but that card should be supported by b43xx driver. 
if that does not work go [here]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working") and follow the instructions on that page.

---

