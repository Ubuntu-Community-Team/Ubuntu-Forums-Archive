---
title: "Automaticly eject Virtual CD on Wifi adapter"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-07-20
This is question and documentation for a part solution for Netgear WNDA3200(Virgin Mobile) adapter.

What is the best way to eject a Atheros Wifi adapter Virtual CDROM?

If just running "eject" is the solution, were is the best or easiest way to put eject in the startup?



I found the eject solution after looking at [http://www.wikidevi.com/wiki/Netgear_WNDA3200](http://www.wikidevi.com/wiki/Netgear_WNDA3200)
 But is also says the ath9k driver should be doing this. 

Linux thinks it's a USB drive until you run eject:

```

 uname -a
Linux max 3.2.0-26-generic #41-Ubuntu i686 i686 i386 GNU/Linux

lsusb
Bus 001 Device 006: ID 0cf3:20ff Atheros Communications, Inc. Virtual
 CD-ROM

iwconfig wlan0
wlan0     No such device

eject
eject: unable to eject, last error: No such device

lsusb
Bus 001 Device 005: ID 0846:9018 NetGear, Inc. WNDA3200 802.11abgn Wireless Adapter [Atheros AR7010+AR9280]

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by bakegoodz on 2012-07-21
The adapter keeps in wifi mode with reboots, but not after being powered off. Not much a concern any more, because I'm stuck on figureing out to make Hostapd work with 11n and 5ghz

---

### Post by bakegoodz on 2012-08-28
While I researching chipsets supported by ath9k I found this page. I found this [http://linuxwireless.org/en/users/Drivers/ath9k_htc#Modeswitching_for_AR7010](http://linuxwireless.org/en/users/Drivers/ath9k_htc#Modeswitching_for_AR7010)

Ah ha I found the proper way to start up the adapter. I didn't need to run "eject" anymore.
```
apt-get install usb-modeswitch
```

---

