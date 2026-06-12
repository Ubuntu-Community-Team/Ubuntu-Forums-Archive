---
title: "Problem with AR5523 (Encore ENUWI-SG) usb wi-fi adapter on Lucid"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by espartano on 2010-06-30
Hello.

I've been following this tutorial [http://ubuntuforums.org/showpost.php?p=9369514&postcount=4](http://ubuntuforums.org/showpost.php?p=9369514&postcount=4) to install the usb wi-fi adapter Encore ENUWI-SG on my Lucid 32bits.

It worked, the usb is recognized, and I can connect to my wireless router. 
The problem is, there is no transmission of data! I am connected, but it's as if I wasn't. Can't access anything.

I know for sure my wi-fi is working fine (my notebook, psp and ps3 all connect with no problems). The antenna is about 50cm from my desktop.

What could be the problem?

Here's the lsusb info:
```
Bus 001 Device 005: ID 0d8e:7801 Global Sun Technology, Inc. AR5523
```

and the iwconfig info:

```
wlan0     IEEE 802.11bg  ESSID:"skynet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:58:3C:23:FB   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks!

---

