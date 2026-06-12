---
title: "Error message with monitor mode"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by Abdujaparov on 2009-09-23
Hi,
I've tried to set my wifi card in monitor mode and I've received this error message:

> 
root@angelo-ubuntu:/home/angelo# iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.


What does it mean?
What can I do to set the card in monitor mode?
Thanks, bye bye.

---

### Post by tgeer43 on 2009-09-23
It means that you cannot change the mode on-the-fly (when it is busy). Try this:
```
ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up
```Note: the first and last commands are i_**f**_config while the middle one is i**_w_**config.

tgeer

---

### Post by Abdujaparov on 2009-09-23
Hi,
I've got this wireless card:

Intel Corporation PRO/Wireless 4965 AG or AGN

How can I see what driver is used?

Thanks, bye bye.

---

