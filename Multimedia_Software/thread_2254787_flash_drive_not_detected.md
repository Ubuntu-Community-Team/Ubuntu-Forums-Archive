---
title: "flash drive not detected"
date: 2014-11-30
forum: Multimedia Software
---

### Post by schimmelpfennig on 2014-11-30
ADATA S107/16GB USB 3.0
when plugging the led goes on and off, and that's it :)

dmesg | tail
[39597.551964] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39597.552001] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39603.559006] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39603.559042] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39609.568204] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39609.568240] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39615.573035] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39615.573070] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39621.579529] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38
[39621.579566] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 2c:e6:cc:d4:70:48   profile =2c:e6:cc:d4:94:38


no idea what to do :D please help! :D

---

### Post by carl4926 on 2014-11-30
Reformat it in Windows if you can
It just eliminates a few posibilities

If you can't do that, can you tell us what format it is. And any history of your use of it before this?

---

### Post by Yellow Pasque on 2014-11-30
It looks like your wireless driver is spamming dmesg. While it may not affect the wireless operation, it will create large log files and it makes it difficult to troubleshoot other issues (like this one) where you want to see the most recent dmesg output.
This may help: [http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console](http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console)

---

