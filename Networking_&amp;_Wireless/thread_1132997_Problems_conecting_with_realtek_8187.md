---
title: "Problems conecting with realtek 8187"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by Chif on 2009-04-22
well i recently installed ubuntu 8.10 to my desktop pc and im having a strange problem here... im using a usb wireless card with realtek chipset, it detects my wireless network and others, but i cant conect to any... it sometimes conects to my network but i have no internet access and it takes a long time to conect, it asks for authentification a lot of times and when it finaly conects i have no internet access...

is this problem because of the signal? coz i have tried a lot of stuff i have seen on forums and ubuntu help but nothing solves the problem... if it is the signal should i buy another wireless card? wich one you recomend??

hope some1 can help me with this problem :)

---

### Post by Chif on 2009-04-23
i forgot to add yesterday that i can conect to my network on windows with no problem... so i think maybe ubuntu has the problem in some configuration or something...

so if any other data is needed just ask i want to solve this plz

---

### Post by heliedgar on 2009-08-30
hi im at the same situation but i have a soution
Try sudo iwconfig wlan0 rate 12M
and then conect.

it work for me

---

### Post by fidelandche on 2009-08-30
If you look at the post I have placed in networking/wireless sub forum, I had a problem where the signal strength was poor, which meant I was unable to connect. Once I entered the code problems solved.
 
[http://ubuntuforums.org/showthread.php?t=1176117&page=5](http://ubuntuforums.org/showthread.php?t=1176117&page=5)

---

