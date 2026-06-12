---
title: "need to active hotspot"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by L!NUX MAN on 2013-05-22
I have a : Network controller: Intel Corporation WiFi Link 5100 wireless device
and I want to run it as accesspoint , I tried to active HotSpot but didn't work

I tried to change the device mode to master , but I canet
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

I have this problem while I trying to change mode

```

sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

I need to active HotSpot and use it like access point

note: the device is working on windows 7 via "virtual route" programe as well , so my device support access point on windows with no problem

---

### Post by L!NUX MAN on 2013-05-23
hey >>> UP

---

