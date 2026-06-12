---
title: "Lost internet connection"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by nano69an on 2011-04-06
Hi,
 
I have been using ubuntu netbook 10.10 on my Dell Mini 9 for the past few month without any problem; it connects wirelessly to the internet via a wireless router. Yesterday in the middle of web surfing, suddently firefox cannot see any website outside of my home network (Firefox displays Server not found page). No help when I rebooted a few times and connect to my home network via wireless or even wire cable; it can access files in my network file server (DNS-321) but not the internet.
 
My desktop computer running Windows Vista and ASUS media player has no problem accessing the internet.
 
Any help would be appreciated.
 
Andy

---

### Post by dineshs on 2011-04-06
Does```
route -n 
```show a gateway?
Can you ping 4.2.2.1?```
ping 4.2.2.1 -c3
```or any site by IP?

---

