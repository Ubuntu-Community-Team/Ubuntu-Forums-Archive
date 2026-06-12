---
title: "Compaq nc6000 Wireless Hard Blocked"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by Sx2Kirby on 2011-08-04
Hey I was messing around with xubuntu trying to get wicd to work with openbox and I seemed to have hard blocked my net card somehow. 
lshw return this:  

```
*-network:0 DISABLED
description: Wireless interface
product: Atheros AR5001X+ Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 4
bus info: pci@0000:02:04.0
logical name: wlan0
version: 01
serial 00:0b:cd:59:99:23
width: 32bits
clock 33Mhz
capabilities: pm bus_master cap)list ethernet physical wireless
configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic
fireware=N/A latency=168 link=no maxlatency=28 mingt=10 multicast=yes wireless=IEEE 802.11abg
resources irq:11 memory:90080000-9008ffff
```

and rfkill list returns:
```

0: phy0: wireless LAN
soft blocke0d: no
Hard blocked: yes
```

---

### Post by Toz on 2011-08-05
A hard block generally means the wireless has been physically disabled (bios or switch).I believe the nc6000 has a wireless switch button just above the keyboard. Is it enabled?

---

