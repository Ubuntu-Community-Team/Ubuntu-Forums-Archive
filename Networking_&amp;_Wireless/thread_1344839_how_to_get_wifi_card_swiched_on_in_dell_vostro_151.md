---
title: "how to get wifi card swiched on in dell vostro 1510"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by vostro1510 on 2009-12-03
I installed ubuntu 9.10 in windows xp service back 3 in my dell vostro, in order to get dual boot option. i am unable to swich on wifi card while using ubuntu . wifi gets switch on when i use windows.

i have Dell Wireless 1395 WLAN Mini-Card  in my system...

pls help me to get rid of this problem

---

### Post by JBAlaska on 2009-12-03
First go to System, Administration, Software Sources and make sure "Proprietary drivers for devices (restricted) is checked.

Then do this in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Reboot Ubuntu

Now go to System, Administration and "Hardware drivers" and check the use Broadcom sta wireless driver. 

Reboot Ubuntu and you should have support for your wireless chipset.

---

### Post by vostro1510 on 2009-12-03
Thankyou

 it worked

---

### Post by JBAlaska on 2009-12-04
Great! Please mark this thread as "Solved" so others can search for it.

---

