---
title: "Intel / Ubuntu 12.04 LTS / Toshiba R705 - Issue with WPA only"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by gamermatt on 2012-06-07
Hello,

I have an issue with my wireless card. I can connect to unsecured networks... but, when I try to connect to my home router (WPA), it does not work. It picks up the network, I entered the password correctly, then it says it connected. But, when I try to load any internet-related task, it will not even begin to load. 
I am able to connect to the router with other wireless devices.

1 ) Machine Brand and Model (PC/Laptop):
```
Toshiba R705-25
```
2 ) Wireless Brand, Model and Wireless Chipset:
```
Intel Corporation Centrino Advanced-N 6200
```
3 ) check interface:
```
wlan0     IEEE 802.11abgn  ESSID:"UCInet Mobile Access"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:A2:FB:D4:D0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2534   Missed beacon:0

```
4 ) Check for modules:
```
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211
```


Any help would be appreciated.

Matt

---

### Post by chili555 on 2012-06-07
Please try this: [http://ubuntuforums.org/showpost.php?p=11995045&postcount=4](http://ubuntuforums.org/showpost.php?p=11995045&postcount=4)

---

