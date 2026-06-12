---
title: "Ubuntu Server 10.04 - acer aspire 3000 wifi"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by eronde on 2010-07-14
Hi, 

For a few days I've been trying to get my wifi card (bcm4318) of a acer aspire
3000 to work. I followed these treaths without any luck:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)


Some info:

```

spci |grep 4318
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

``````

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: ssb)

```without loading b43-module
```

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```without loading b43-module
```

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"My_card"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


```When I look in dmesg, it says that the link is not ready.
```

 b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  911.614419] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  911.620934] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  911.627301] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  911.757945] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  911.806817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  911.828158] b43-phy0: Radio hardware status changed to DISABLED

```On a forum I've read that you must install acerhk to enable your wificard, but the software doesn't support the aspire 3000.

Does anyone have a idea how I  could get my wifi-card to work?

---

