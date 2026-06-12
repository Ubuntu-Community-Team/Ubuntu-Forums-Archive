---
title: "Wireless network not detected after wakeup"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Psychs on 2010-05-15
I am using a Toshiba Satellite M200. Sometimes after a wakeup ubuntu does not detect any wireless networks. This does not happen all the time only some times but, when I restart my computer the wireless networks are detected.

Can any one tell me how to correct it.  I do not restarting the computer again and again.

---

### Post by kid1000002000 on 2010-05-15
Occasionally, I have to right click on the network manager icon in the top panel of Ubuntu and enable wireless or networking.  That could solve your problem.  You could also try enabling wireless from the command line as well; there are plenty of tutorials to learn how to do that and it might help you to diagnose the problem a little bit better.

---

### Post by chili555 on 2010-05-15
Here is a technique that works for many. Please open Applications > Accessories > Terminal and do:```
sudo lshw -C network
```You will learn details about your wired and wireless card. For example, here is my wireless detail. You need the exact name of your wireless driver.> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       --- snip ---
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.108 Next do:```
sudo gedit /etc/pm/config.d/config
```The text editor gedit will open. Type in:```
SUSPEND_MODULES="iwl3945"
```Substitute the driver name you found. Proofread carefully, save and close gedit. 

Suspend and report your success.

---

