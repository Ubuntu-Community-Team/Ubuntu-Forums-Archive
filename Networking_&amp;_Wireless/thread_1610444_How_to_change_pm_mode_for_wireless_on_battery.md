---
title: "How to change pm mode for wireless on battery?"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by sidowaty on 2010-10-31
Hi all!

Hardware: Vostro 3500, BCM4353
Ubuntu 10.10

Today I decided to test uptime on battery. But when I started using battery I noticed that internet connection is very slow(around 1-4 KB/s, normally ~128KB/s). 

I used 
```
iwpriv eth1 set_pm 0
```
(pm = power mode? And what means this parameter 0, 1 and 2?)
and everything seems to be ok now. And my question is - where can I edit which power mode settings for wifi are used on battery?

Thanks!

---

### Post by dorpm on 2011-01-14
Of course you can. Please refer to [B]/usr/lib/pm-utils/power.d/wireless

[/B]Cheers,
Florian

---

