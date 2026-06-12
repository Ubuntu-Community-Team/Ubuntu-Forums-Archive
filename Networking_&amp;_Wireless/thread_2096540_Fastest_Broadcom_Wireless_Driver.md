---
title: "Fastest Broadcom Wireless Driver"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by sml on 2012-12-20
There are a few different Broadcom wireless drivers options.

Which one should I use for the best performance ... speed and battery life?

wl - Proprietary Broadcom STA Wireless driver 

b43 - Open source driver

brcmsmac (a.k.a brcm80211) - Open source driver from Broadcom (merged into kernel 2.6.37)

---

### Post by Pjotr123 on 2012-12-20
Proprietary. Usually the best choice.

---

### Post by chili555 on 2012-12-20
Very few devices work perfectly well with either driver. With one driver, an interface may be created, wlan0, for instance, but it may never actually connect. Switching to the preferred driver connects smoothly. As well, there are some devices that can only be driven by one driver but not at all by the others. Here is an informative wiki page: [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

In my somewhat limited experience, I am not yet aware of *any* device that works correctly with brcmsmac. However, the day is young and I learn something new every day.

---

