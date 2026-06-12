---
title: "How do I force wireless N mode?"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by spitfirejunky on 2012-05-12
So after God knows how much tweaking, I finally got my SMCWUSB-N2 USB Wi-Fi dongle to have a 100% stable internet connection with my router, Cisco Linksys E1200 using ndiswrapper under Ubuntu 12.04 x86_64.

The carl9170 driver packaged with Ubuntu is supposed to work with the dongle's chipset but the router must be put in wireless G mode, the driver fails to hang on to the internet connection for longer than 2-3 minutes, and DHCP reservation breaks for some reason.

As a last resort, I followed the stickied thread for installing ndiswrapper from source and I used the 64-bit XP drivers distributed by the SMC site to establish another connection. This connection is 100% stable and works with all the router's features except wireless N mode.

Seeing as I got this dongle for the sole purpose of upgrading the LAN to wireless N, I'd like to know if there is a way I can configure some part of the system to force wireless N mode.

The dongle works perfectly in wireless N mode under Windows 7 64-bit.



lshw -C Network
```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:2d:28:7e:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+arusb_xp driverversion=1.57+,11/30/2008,3.0.0.136 link=yes multicast=yes wireless=IEEE 802.11g

```

lsusb
```

Bus 002 Device 004: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]

```

---

### Post by spitfirejunky on 2012-05-12
UPDATE:

Turns out wireless-N itself was the issue all along.

I put the router in wireless-G only mode (not mixed or wireless-N) and gave the carl9170 driver a second chance after reading that the carl9170 was not programmed with a wireless-N solution, or at least one that's standards compliant.

So the only shot I have at getting wireless-N working is with ndiswrapper, and I have no idea how.

So to repeat:

Both ndiswrapper and carl9170 work perfectly on wireless-G access points.

---

### Post by spitfirejunky on 2012-05-13
UPDATE:

So I performed the following on both the working ndiswrapper drivers and carl9170:

```
sudo iwlist scan
```

This displays the supported "Bit Rates" on the working wireless interface as they correspond to the current driver.

To no surprise, not a single driver can function higher than 54 Mb/s, which is why the router must be throttled to wireless-G.

Mystery solved and I feel shafted. =(

---

