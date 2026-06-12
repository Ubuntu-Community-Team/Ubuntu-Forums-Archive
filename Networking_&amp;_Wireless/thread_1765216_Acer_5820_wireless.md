---
title: "Acer 5820 wireless"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by graphius on 2011-05-22
I bought my son an Acer 5820T laptop. He prefers Ubuntu over windows, but I can't get the wireless working. 
This model has a Broadcom bcm43225 card, which I understand is problematic. I have tried a bunch of solutions posted, but nothing seems to work.
If I do a rfkill list I get
> 0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


It seems like the driver works for a second and then crashes.

Any suggestions?

---

### Post by josephmills on 2011-05-22
> **graphius said:**
> I bought my son an Acer 5820T laptop. He prefers Ubuntu over windows, but I can't get the wireless working. 
This model has a Broadcom bcm43225 card, which I understand is problematic. I have tried a bunch of solutions posted, but nothing seems to work.
If I do a rfkill list I get


It seems like the driver works for a second and then crashes.

Any suggestions?

try```
 rfkill unblock all 
``` could we also see a ```
dmesg | grep wl
``` and ```
lsmod
``` thanks

---

