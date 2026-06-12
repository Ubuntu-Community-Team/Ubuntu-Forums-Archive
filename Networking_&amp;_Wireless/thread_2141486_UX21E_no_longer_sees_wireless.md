---
title: "UX21E no longer sees wireless"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by Wosco on 2013-05-02
Hi All

My wireless card was working.

I am running Ubuntu 13.04, thought I'd try installing Atheros windows drivers for my wireless card using Ndisgtk (mistake). After installing winodws Atherso drivers it didn't work of course, so I removed the driver it installed and now I cant connect to wireless at all. I don't even have the option to enble wireless. 

Reboot doesn't re enable it either. 

Any help greatly appreciated.

ASUS UX21E 64Bit Ubuntu 13.04

Regards
Wosco

---

### Post by Wosco on 2013-05-02
Appologies I got information from a response below and fixed the problem

---

### Post by Wosco on 2013-05-02
Oops... I spoke too early, whenever I reboot my Asus UX21e it looses the wireless card/network. There is no option to enble wireless.

If I enter this into a command line:

sudo modprobe -r ath9k
sudo modprobe ath9k blink=1

It starts up until I reboot, then the process re occurs

Anyone able to tell me how I can fix this please

Thanks
Wosco

---

