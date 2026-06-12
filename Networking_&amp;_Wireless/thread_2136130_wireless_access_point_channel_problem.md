---
title: "wireless access point channel problem"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by RCSub on 2013-04-16
Hi everyone

Some quick info:
Dist: ubuntu 12.04.2 LTS - server 32 bit
Wireless card: Intel Centrino Advanced-N 6235
Wireless driver: iwlwifi

I have setup my system with hostapd and dnsmasq to act as a wireless access point. On 2.4GHz channels 1-11 in 802.11g mode, this works flawlesly. But I am unable to set it into 802.11a mode using a 5 GHz channel.

output from hostapd:
```
wlan0: IEEE 802.11 Configured channel (48) not found from channel list of current mode (2) IEEE 802.11a
wlan0: IEEE 802.11 Hardware does not support configured channel
Could not select hw_mode and channel. (-1)
wlan0: Unable to setup interface.
[ 1062.871672] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
```

when I run "iw reg get" it shows my region (DK) correct with correct channels allowed, but when I run "iw list", my entire Band 2 (5 Ghz band) is "passive scanning, no IBSS" and some are "passive scanning, no IBSS, radar detection"

Any help is appreciated




ps. I went through modifying my regional regulations following this:  [http://www.backtrack-linux.org/forums/showthread.php?t=16658](http://www.backtrack-linux.org/forums/showthread.php?t=16658) only I modified the db.txt and compiled it before making and make installing CRDA. Before this my iw reg get was wrong too.

---

### Post by RCSub on 2013-04-16
Have anyone seen something similar?

Does anyone know of a mini pci-e half/full or 1x pci-e card that supports 802.11a and 802.11g, and can run hostapd in 802.11a mode ?

Does anyone know if it would possibly help to install an older version/other distribution of ubuntu/linux

---

