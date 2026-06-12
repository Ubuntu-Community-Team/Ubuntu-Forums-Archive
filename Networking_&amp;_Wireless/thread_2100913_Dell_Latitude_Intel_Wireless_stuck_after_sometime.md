---
title: "Dell Latitude Intel Wireless stuck after sometime"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2013-01-03
Hey,

My machine is Dell Latitude E6410 and Ubuntu is 12.04.

My wireless works fine but if i put on torrent download / upload then after a random period of time the wireless gets stuck and does not restore even if i restart the networking services. Only solution at that point reverts to restart the laptop and then it gets working again. Is this some driver related problem.???

Output of lshw is below for reference:

sudo lshw -c network
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:63:6d:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic-pae firmware=9.221.4.1 build 25532 ip=192.168.100.21 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:94100000-94101fff

---

### Post by anspectrum on 2013-01-07
Bump....:(

---

### Post by bkratz on 2013-01-07
Have you tried disabling the "N" mode in iwlwifi yet? It seems to help Intel wireless cards. See

[http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable%3D1](http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable%3D1)


see posts 2 and 4

---

### Post by anspectrum on 2013-01-08
Thank you bkratz. Chili555 does love UBUNTU alotttt.

:lolflag:

---

### Post by bkratz on 2013-01-08
> **anspectrum said:**
> Thank you bkratz. Chili555 does love UBUNTU alotttt.

:lolflag:



Hope it helped you! Dr. Chili sure does, and hopefully you will too. We can all learn a lot from him ( esp. patience and manners! )

---

