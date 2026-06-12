---
title: "Can't connect to internet via ppp0 while wlan0/eth0 is connected"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by gioman22 on 2011-01-16
Hi,

I can't seem to connect to the Internet using my 3G card while my wireless is connected. I don't want to share my 3G Internet connection I just want them connected simultaneously and for PPP0 to be used as the default Internet connection. 

I can see in the notification bar that both networks are active but its as if ubuntu is trying to connect to the Internet through my wireless connection(Connected to a router/switch) once I disconnect from the wireless I can browse the Internet again using the internal 3G card... I've tried using fire starter to get around this but It still wont connect through ppp0 while wlan0 is connected.

Any help, its driving me crazy

---

### Post by Trevor_Jones on 2011-06-20
Anyone found an answer to this one?
I have the same problem I'm trying to setup a local hotspot. My internet connection is via ppp0 and my wireless network card is on wlan0. I can acquire connections on either but I cannot get both of them up together. If I have an internet connection on ppp0 Firestarter reports:
Internal network device wlan0 is not ready. Aborting
If I connect on wlan0 then i get:
External network device ppp0 is not ready. Aborting.
Help!

---

