---
title: "Access points with same ESSID ?!?"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by alimahmoudy on 2009-04-22
Hello, i connect using a wireless connection with a WEP key encryption.
The problem is, there are two access points in my area with the same name, dlink. 
I cannot change the ESSID for any one of the access points, and I've tried manual configuration, but it's still causing me trouble. Sometimes it works, sometimes it doesn't.
I tried positioning my usb wireless card (in order to get a better signal for my access point) but the problem persisted.
When i boot windows i can normally connect using a network manager (ZDWLAN), i know the right access point by the BSSID.
Any ideas ? this is really confusing and frustrating ! thanks in advance.

---

### Post by alimahmoudy on 2009-04-22
Sorry about that. But i found the solution. For anyone who's interested, 
switch to manual configuration, and select the ESSID, i had to try them both.
Then use the command 
sudo iwconfig eth0(or wlan0 depending on your card) ap mac

example:

sudo iwconfig eth0 ap 12:11:11:23:11:11

---

### Post by elewton on 2009-04-22
Thanks, man.  That'll be  useful to me.

---

