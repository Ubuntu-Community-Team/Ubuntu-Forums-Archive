---
title: "KUbuntu 10.10 Laptop CQ40-324TU Wireless"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by gnulab on 2010-10-08
Hi Guys,

Just want to report what my laptop had gone through in order to set up my wireless. I'm a newbie, so pardon if certain things are redundant.

I'm using Kubuntu 10.10, nothing modified and installation went alright. 
Ethernet checked.
Sound checked.
Wireless fail.

Anyway, CQ40-324TU is using this type of Broadcom.

```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

Upon completing fresh install of KUbuntu 10.10, the system is using the b43 driver.

I decided to use the **ndiswrapper** method to get my wireless working. I religiously follow the ndiswrapper sticky at [http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847") but I was still stuck. Turns out it was the Windows 7 drivers (hey, I thought Windows XX driver is universal) and that's why wlan0 doesn't appear at the Network Management.

Once I installed the Windows XP driver, reboot. Wlan0 is up. :D

Hope this helps.
Henry

---

