---
title: "RTL8187B USB dongle drops connection on Ubuntu 10.04."
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by jackyboy633 on 2011-07-08
Hello everyone!

I have a problem with my LogicPro Linux compatible wireless adapter that uses the RTL8187B chipset. Basically, when I connect, it stays connected for a few minutes, then it drops. I then reconnect the first time, which worked OK, then it dropped. This happens again and again, which can be a nuisance when downloading updates or other distros. After a few of these cycles, it refuses to connect unless I unplug and replug my dongle. Here is some information:

PC model: Fujitsu-Siemens Scenic P320.

Lsusb results: Bus 001 Device 005: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

Interface check:
wlan0     IEEE 802.11bg  ESSID:"mynetwork*"
          Mode:Managed  Frequency:2.472GHz  Access Point:Not-Associated
          Tx-Power 20dBm
          Retry  long limit=7  RTS thr=off  Fragment thr=off
          Power management=off

Modules check: rtl8187

Ubuntu and kernel version: Ubuntu 10.04 (lucid) 2.6.32-32 generic i686.

Any help will be appreciated. :KS

Regards, Jackyboy633

---

### Post by jackyboy633 on 2011-07-08
By the way, the router uses WPA/WPA2 encryption.

---

