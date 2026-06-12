---
title: "Unable to get the specific AP info via &quot;iwlist wlan0 scanning&quot;"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by nakoruru on 2010-11-03
Hi, i have a router with wireless on,and i want to get the ap information via "iwlist wlan0 scanning",but seems the scan result does't contain the ap info i want. meanwhile, the cell phone can get the router ap info, does anyone encounter same questions? and how to resolve? i try to reboot the PC or router, but it doesn't work.

---

### Post by nakoruru on 2010-11-03
i got some new informations. but also got some new questions.
 
1.when the ap is in the 13 frequency band, i can't get the ap info via iwlist scanning. which is very weird.
 
2.Given that the i get the ap info of my router which is in frequency band 1, then i change the router to frequency band 13, but when i execute "iwlist wlan0 scanning" , i still find that the ap is in frequency 1. i guess the wifi doesn't "really" scan the ap around but instead,it just get the result from cache, if it's true, how to clean the cache and make the wifi do a "real" scanning.

---

### Post by grahammechanical on 2010-11-03
What particular information are you seeking? Are you looking for information about your own setup or about nearby wireless Access Points?

Check out the Wireless Trouble Shooting Guide at

[HTML]https://help.unbuntu.com/community/WifiDocs/WirelessTroubleShootingGuide[/HTML]Regards

---

### Post by nakoruru on 2010-11-03
thanks for your reply, i am seeking for the information about my own wireless setup to sovle the 2 weird issue:
1. unable to get the nearby ap info which is in 13 frequency band.
2. when a nearby ap change it's frequency band from other to 13, the ap is still found in it's original band by executing"iwlist scanning ", but actually unable to connect.

---

### Post by chili555 on 2010-11-03
> i guess the wifi doesn't "really" scan the ap around but instead,it just get the result from cache, if it's true, how to clean the cache and make the wifi do a "real" scanning. Here is a quote from *man iwlist*:> Triggering  scanning  is a privileged operation (root only) and normal users can only read left-over scan results.The short answer is:```
***sudo*** iwlist wlan0 scan
```

---

### Post by nakoruru on 2010-11-03
thanks chili555^^, but i do run the command as root, so i guess i actually get the latest ap info, and i also try "sudo iwlist wlan0 scanning", but get the same result:).
 
below is the detailed phenomenon:
 
first,i change the router to frequency band 6 (namely channel 6), and my wifi can find it and show that it is in frequency band 6, now i change the router to band 13(or 12), my wifi still find it , but it show that the route ap is still in band 6, this should be wrong. and after a period of time, the route ap info disappeared.
if i change the route to other band such as 1,or 9, wifi can discover the change immediately.
 
so i conclude that the wifi i used is unable to detect the ap info which in frequency band 12,13, and the wifi doesn't clean the ap info which is already unavailable in times.
 
any advices? thanks^^:guitar:

---

