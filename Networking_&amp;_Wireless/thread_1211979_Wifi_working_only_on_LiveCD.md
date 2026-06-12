---
title: "Wifi working only on LiveCD"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by lambdacore on 2009-07-13
ok so i have an Eee PC 1000 HA and everything was working fine. the wifi was wlan0.

then, i messed around a bit with ifconfig and iwconfig to have fun with aircrack.

but when i rebooted, the wifi was no longer working.
wlan0 does not exist.
modprobe wlan0 returns error saying module not found etc.

but when i boot from my usb LiveCD, the wifi works just fine.
so it's like deactivated or crap.

i check the bios, wifi is enabled.

what the hell?

---

### Post by superprash2003 on 2009-07-13
post output of
1)lshw -C network
2)iwconfig

---

### Post by lambdacore on 2009-08-11
hey it's been a hell of a while.
i had to reinstall my ubuntu in order to make it work.
since then i did not use aircrack again because i did not feel like losing my wifi again.
but the temptation was too strong and i did it again. and i again lost my wifi in the same way.

but this time, like last time, i went in /etc/modprobe.d to look at the blacklists.
and there was one that was not there before.
madwifi.conf
and ath5k was not commented. i commented it, and wifi is back like a charm.

so if it ever happens to anybody.

---

