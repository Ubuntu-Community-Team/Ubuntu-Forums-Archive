---
title: "how can fix eroor no such devis"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by homa2142 on 2010-09-30
hi i installed my wifi driver corectly
why i have this eroor
Interface    Chipset        Driver

root@rostam-laptop:~# airmon-ng start wlan0


Interface    Chipset        Driver

wlan0            b43 - [phy0]/usr/local/sbin/airmon-ng: 856: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)

..................................................................
wlan0     Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:22ff:fe33:4455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:818103 (818.1 KB)  TX bytes:278957 (278.9 KB)

---

