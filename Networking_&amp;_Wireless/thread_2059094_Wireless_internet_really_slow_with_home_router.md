---
title: "Wireless internet really slow with home router?"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by rEgonicS on 2012-09-17
Hey, I've recently installed Ubuntu 12.04 LTS on my laptop and I've been getting terrible download speeds when connected to my router. The speeds are normal when I'm connected to my college's wifi. Anyone know what may be the issue?

wireless card: Intel Wireless Centrino-N - 1000
router - Linsys WRT300N running DD-WRT

*The router is only an access point for my college's internet.

---

### Post by yasink on 2013-05-07
I have the same problem.  I have Lubuntu.  My internet speed with this machine at home is around 10 times slower than my Mac OS operated desktop. Not only that, when I take this machine with Lubuntu outside and connect to library wireless, it is again 10 times faster.  yasin@yasin-Lenovo:~$ lsusb Bus 001 Device 002: ID 5986:0241 Acer, Inc BisonCam, NB Pro Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  yasin@yasin-Lenovo:~$ iwconfig wlan0     IEEE 802.11bg  ESSID:"BELL111"             Mode:Managed  Frequency:2.437 GHz  Access Point: 3C:EA:4F:28:F3:E1              Bit Rate=24 Mb/s   Tx-Power=20 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off           Link Quality=70/70  Signal level=-21 dBm             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:59  Invalid misc:265   Missed beacon:0  lo        no wireless extensions.  eth0      no wireless extensions.

---

