---
title: "Constant wireless disconnecting with Intel based card"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by naomarik on 2010-05-02
Hi!

This is a fresh install of Ubuntu 10.04 on a Dell XPS M1530. I'm getting very frequent disconnects to my wireless network, despite good signal. I have wicd and nm-applet running side by side, wicd doesn't work by itself and nm-applet won't get a new IP after reassociating with the AP. I don't really know how to go about troubleshooting this, so included some information I thought would be helpful. 

Wireless connection is steady in Windows 7, so I'm guessing it's a problem with the driver.

Wifi card:
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Driver: 
```
[   22.889588] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 2.6.32-21-generic-ks
[   22.889592] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   22.946985] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
```

Output from dmesg I thought would be helpful:



```
[ 1671.836485] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1673.184605] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.200067] wlan0: direct probe responded
[ 1673.200076] wlan0: authenticate with AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.216926] wlan0: authenticated
[ 1673.216949] wlan0: associate with AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.223588] wlan0: RX AssocResp from 00:1e:e5:f5:f0:31 (capab=0x411 status=0 aid=4)
[ 1673.223594] wlan0: associated
[ 1673.226174] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1673.400314] wlan0: deauthenticating from 00:1e:e5:f5:f0:31 by local choice (reason=3)
[ 1673.667945] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1673.671302] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.673791] wlan0: direct probe responded
[ 1673.673800] wlan0: authenticate with AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.680055] wlan0: authenticated
[ 1673.680185] wlan0: associate with AP 00:1e:e5:f5:f0:31 (try 1)
[ 1673.685641] wlan0: RX AssocResp from 00:1e:e5:f5:f0:31 (capab=0x411 status=0 aid=4)
[ 1673.685650] wlan0: associated
[ 1673.688816] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1673.872681] sky2 eth0: disabling interface
[ 1673.886456] sky2 eth0: enabling interface
[ 1673.887806] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1673.921264] wlan0: deauthenticating from 00:1e:e5:f5:f0:31 by local choice (reason=3)
```



```
[ 1997.542439] No probe response from AP 00:1e:e5:f5:f0:31 after 500ms, disconnecting.
[ 1998.960530] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 (try 1)
[ 1999.160105] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 (try 2)
[ 1999.360203] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 (try 3)
[ 1999.560067] wlan0: direct probe to AP 00:1e:e5:f5:f0:31 timed out

```

---

### Post by naomarik on 2010-05-02
Found a bug post where people have same problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035)

---

### Post by cristianrosa on 2010-05-06
It may also be this bug [#348204]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all")

---

