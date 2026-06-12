---
title: "wireless driver is blacklist"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by R6_68 on 2010-07-09
hi
I search forum , but can not find anything

one :
I have , acer 5315 , wireless is broadcom 802.11b/g

ubuntu find this , but I cant active it 


" broadcome sta wireless driver "

and say read log file, and at log file , say :
" BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted "

last 3 day , wireless is work, but when update ubuntu, my wireless is deactive !!

two :
when I connect to wireless network, my dsl connection was not shown , my network is bridge and need too connection to connect to internet , 
only connect with lan, my connection was shown !!

tnx

---

### Post by Iowan on 2010-07-09
I probably missed something in the information, but...

some updates disable networking - right-click on Network Manager icon and verify that the Enable Networking box is checked.

From a terminal (Applications>Accessories>Terminal), **sudo lshw -C network** should provide information about your interfaces - including which (if any) driver is being used.

---

