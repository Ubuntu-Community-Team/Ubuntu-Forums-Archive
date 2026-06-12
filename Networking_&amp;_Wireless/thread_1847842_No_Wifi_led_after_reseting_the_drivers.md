---
title: "No Wifi led after reseting the drivers"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by klov on 2011-09-21
Hello All,

My iwconfig was giving eth1  unassociated. But thanks to [**praseodym**]("http://ubuntuforums.org/member.php?u=1411497")'s help , I fixed it on this [thread]("http://ubuntuforums.org/showthread.php?t=1847771&page")  .

But now the wireless led isn't blinking.
lsmod | grep 2200 gives output
```

ipw2200     134333 0 
libipw            40328  1 ipw2200
cfg80211    144266 2  ipw2200, libipw
lib80211        5110   3  lib80211_crypt_wep, ipw2200, libipw
compact_firmware_class 6554 1 ipw2200

```

 I tried to add libipw, cfg80211 , lib80211 to blacklist, but doesn't help.

sudo apt-get install linux-backports-modules-wireless-lucid-genericadded compact_firmware_class 6554 1 ipw2200 and I guess lib80211. So tried to blacklist, but didnt help.
Also tried sudo ifdown eth1 and then sudo ifup eth1.
nm-tool
```

State : connected
---Device : eth1 ---
type 802.11 Wifi
driver: ipw2200
State : disconnected

```


Is there anything I can try to get the state to connected.
Will appreciate any further help

---

