---
title: "broadcom 4313 blocking other wifi users"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by trolson on 2013-04-01
When I'm connected to wifi by broadcom 4313 other wifi users have very limited speed. I'm not downloading or uploading anything but other computer (win7) has speed about 0.5Mb/s. If I dosconnect the speed goes to 10Mb/s (testing via [http://speedtest.net](http://speedtest.net)).
I've tried to switch drivers but not I'm lost and even dont know where I stand with this...
Thanks for help.

edit:
solved by:

1. added to /etc/modprobe.d/blacklist.conf:
```
blacklist bcm43xxblacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper
blacklist wl

```

2. added to /etc/modules:
brcmsmac

3. restart

---

