---
title: "Atheros and wlanconfig for wlan0??"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by GuyWires on 2009-02-14
well I switched to Jaunty alpha 4 but that didn't change anything...

my wireless used to be wifi0 and ath0 but now its wlan0 and wmaster0 so something has changed.

I need to change my MAC for public hotspots and anti-spoofing at home, but there is a problem with doing that cause after I do it using macchanger I can't get IP address from ap dhcp or something... it just doesn't work :s

when I use wlanconfig to destroy the VAP wlan0 and then try to change MAC of wmaster0 all I get is wlanconfig: ioctl: Operation not supported

Should I file bug report or does someone else want too or is there a simple fix?

please help cuz the "1337 h4x0rs"(pfft) on my block keep messing with my connection, grrr.

oh and yes, i've tried ifconfig wlan0 hw ether <MAC> with no connection either

I've tried to backport the old ath_pci module but then I can't connect with my real MAC... *sigh*

```
lshw
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wmaster0
       version: 01
       serial: needs changing...
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.66 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11abg
```

---

### Post by GuyWires on 2009-02-14
bold subject line needed?

---

### Post by GuyWires on 2009-02-14
Looks like I'm not the only one wondering wth...

[http://ubuntuforums.org/archive/index.php/t-1014355.html](http://ubuntuforums.org/archive/index.php/t-1014355.html)

---

