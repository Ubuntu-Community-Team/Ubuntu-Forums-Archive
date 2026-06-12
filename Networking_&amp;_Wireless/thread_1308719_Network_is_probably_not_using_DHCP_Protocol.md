---
title: "Network is probably not using DHCP Protocol"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Juhnstun on 2009-10-31
I am new to Ubuntu. A few weeks ago, computer stopped connecting to the internet. Just upgraded to 9.10 and during the instal, the autoconfig gave message:
 
Network is probably not using the DHCP server or DHCP server may be slow or some network equiptment is not working properly. 
 
I finished the instal and sure enough, the internet still does not work 
 
The top panel says the wired network is disabled. I typed lspci in terminal and it appears to recognize the Intel Bridge I am using as a wireless receiver. 
 
Don't know if I need drivers or other commands to see if it recognizes the network card. Any help much appreciated!

---

### Post by Iowan on 2009-11-01
Unfortunately, 9.10 networking seems a bit marginal - but updates are being released to fix problems.  **lshw -C network** should tell you if the interface is recognized, has an alias (like wlan0) and a driver attached.

---

