---
title: "broadcom sta wireless driver issue"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by abhinav90 on 2010-08-03
I recently installed ubuntu 10.4 on my dell e6400. i activated the broadcom sta wireless driver from hardware drivers section and the wireless started working. When i restarted my computer, wireless was no longer there as an option. I checked in the broadcom sta wireless driver under hardware drivers and it was written driver active but not currently in use. When i remove and reactivate the driver the wireless again starts working. However, on reboot i get the same issue.

Please help me out with this really odd behaviour.

---

### Post by abhinav90 on 2010-08-08
*ping*

---

### Post by snowpine on 2010-08-08
A bug. :( 

See the documentation at: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by abhinav90 on 2010-08-08
i had a look at the documentation, but it does not mention anything about the issue i am having

---

### Post by snowpine on 2010-08-08
What is the output of this command to identify your specific card?

```
lspci -vvnn | grep 14e4
```

(Applications, Accessories, Terminal)

---

### Post by abhinav90 on 2010-08-09
The out put i got by typing "lspci -vvnn | grep 14e4" was:

```
 abhinav@abhinav-laptop:~$ lspci -vvnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
 
```

---

### Post by snowpine on 2010-08-09
Here are the instructions for installing the Broadcom STA hybrid driver for Dell 4312:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers)

---

### Post by abhinav90 on 2010-08-20
The driver is installed according to the instructions in the documentation as you mentioned. However, everytime i restart the computer, the driver becomes "active but not currently in use". I have to disable and re-enable the driver to make it work everytime on boot.

---

