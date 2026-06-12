---
title: "Netgear WNDA 3100 v2 wireless adapter doesnt connect at startup"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by jaywolff5 on 2012-03-10
I am running
Ubuntu 11.10 (32-bit) dualboot also have xp on a separate harddrive
On a dell Dimension 4600 pc
Netgear WNDA 3100 v2 wireless adapter


I was able to get my wireless connection up and running, but my problem is everytime I turn on my PC I see in the network manager it doesnt search for any wireless networks. I then run Windows Wireless Drivers. And i see the currently installed driver bcmwlhigh5.inf and the hardware is present i have to remove the driver and install it again , then it automatically connects to my wireless network. Im glad i can figure out how to get it to work but this is annoying to have to do everytime i boot up. Does any1 know how to bypass this so it automatically connects once i turn on the pc? Ive also tried using another network manager Wicd but i cant even connect to my network using that it gives me an invalid password error.

---

### Post by chili555 on 2012-03-10
Please open a terminal and try this:```
sudo su
echo ndiswrapper > /etc/modules
exit
```Reboot and let us have your report.

---

### Post by jaywolff5 on 2012-03-10
It worked perfectly. Thank you very much.

---

