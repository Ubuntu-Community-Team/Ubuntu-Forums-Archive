---
title: "problem with hostapd"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by aqkshin on 2013-08-29
I want to create hotspot with ubuntu 13.04, and I found some articles suggesting hostapd for this. After installing and configuring hostapd, I still cannot get it working. The error I get when I run hostapd is

```

sudo hostapd /etc/hostapd.conf 
Configuration file: /etc/hostapd.conf
Could not set channel for kernel driver
wlan0: Unable to setup interface.
Could not connect to kernel driver.

```

my hostapd.conf file is:

```

interface=wlan0
driver=nl80211
ssid=test
channel=1

```

info about my network card/driver:

```

lspci -k | grep -A 3 -i "network"
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
    Subsystem: Dell Latitude E6410
    Kernel driver in use: e1000e
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
--
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
    Kernel driver in use: iwlwifi
03:00.0 CardBus bridge: Ricoh Co Ltd CardBus bridge (rev 02)

```


Could somebody help me?

---

### Post by GwL3eNC on 2013-08-29
I don't have experience with hostapd, but your message tells you

"Could not set channel for kernel driver"

which you set to 1. Is this the channel your wlan operates on? you can find out the channel with 

iwlist scan

Also i'm not shure about the driver you set. Your lspci shows iwlwifi, but like i said i'm
not shure. A mode like hw_mode=g i also cant see in you file

---

### Post by sbnwl on 2013-08-29
Would you mind if I suggest you to try these instructions:
[http://ubuntuforums.org/showthread.php?t=2165035](http://ubuntuforums.org/showthread.php?t=2165035)

Make sure you delete all manually configured hostapd files and uninstall hostapd first, and then you follow the instructions in the given link.

---

### Post by aqkshin on 2013-08-29
Thanks a lot for the replies. 
the ppa ap-hotspot seems to be a great tool. Unfortunately, I could not use it. Running the ap-hotspot configure, showed me in red that "Your wireless card does not support Access Point mode." At least now I know that why I couldn't make hotspot.

---

