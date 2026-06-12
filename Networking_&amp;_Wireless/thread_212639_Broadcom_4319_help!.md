---
title: "Broadcom 4319 help!"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by stevieb on 2006-07-10
Hi,

I have a Lenovo 3000 C100 with a 4319 card.  I've blacklisted bcm4xx, ndiswrapped both bcmwl5 and bcmwl5a in different attempts, but the device still does not show up in Network Settings.  I have been plowing through the forums all weekend and have tried several different howtos on this, but no luck.

Here's the code I got on my most recent attempt (bcm4xx already blacklisted):

```
sudo ndiswrapper -l
No drivers installed

sudo ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

sudo ndiswrapper -m
modprobe config already contains alias directive

sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present
```

what am i doing wrong?:confused: 
-steve

---

