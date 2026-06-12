---
title: "Wireless Issue"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by randomise on 2010-12-20
Hello, I recently decided to dual boot ubuntu 10.10 with windows 7 professional.  I've run into an issue which i cannot solve.  Ubuntu refuses to connect to my network. It's WPA Personal and I've entered the details in numerous times... so its not my fault (I think).  When i enter the details and click OK, the icon at the top moves but after 30 seconds it says i'm disconnected.
  
I've gone through several posts about how to fix this and nothing works.  I've edited a file which supposedly disables wireless N (oh my access point has Wireless G and N... and my card is N also) and that file is located in /etc/modprobe.d/intel-5300-iwlgan-disable11n.conf.... please help.. linux looks really good.. its just bugging me that i can't use the internet on it.

I've also connect to my old broken router which has no security on it and ubuntu connected to that within seconds.  I'm lost.

The router is not broken as every device can still use the internet.

---

### Post by grahammechanical on 2010-12-20
You do not say if you are trying to connect through wireless or wired (ethernet). Can you try with an ethernet cable?

Can you enter in a terminal nm-tool?   Look and see what output you get. You want to see UP and RUNNING alongside eth0, eth1, and wlan0. If UP is not there then these adapters are switched off. If RUNNNING is not there, then you are not connected to the router.

If you are trying to connect by wireless try typing rfkill list. If the output says Soft Blocked: Yes or Hard Blocked: Yes, then the wireless adapter is turned off in software or hardware.

Regards.

---

