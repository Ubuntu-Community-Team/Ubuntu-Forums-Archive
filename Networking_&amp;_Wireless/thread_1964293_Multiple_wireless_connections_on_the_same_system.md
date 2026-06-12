---
title: "Multiple wireless connections on the same system"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by ProDG_Yodha on 2012-04-23
Hi,

I bought a new wireless dongle for my laptop and when I connected it didn't go up. When I checked dmesg, it said it connects to wlan1 instead of wlan0 in both. I know that I could change the scripts and boot up wlan1 instead of wlan0 in both, but I would really like to know where Ubuntu associates the wlan(#n) with a particular MAC ID. 

Also, I don't use Network Manager and do all the setting up in /etc/network/interfaces.

Does anyone know how to reassign wlan0 to my new dongle?

Thanks in advance.

---

### Post by chili555 on 2012-04-23
/etc/udev/rules.d/70-persistent-net.rules

---

### Post by ProDG_Yodha on 2012-04-24
Thanks.

---

