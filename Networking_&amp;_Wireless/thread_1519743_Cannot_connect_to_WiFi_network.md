---
title: "Cannot connect to WiFi network"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by bosbeemer on 2010-06-28
I have a usb Wireless N card. ```
lsusb
``` returns the following - 

```
 Bus 002 Device 003: ID 0bda:8171 Realtek Semiconductor  Corp
```It uses the r8192s_usb driver.

I have followed all the instructions on this thread -

[http://ubuntuforums.org/showthread.php?t=1451484](http://ubuntuforums.org/showthread.php?t=1451484)

and all the other threads that were  mentioned recursively, from one thread to next. 

I did get my wireless card to come up and find wireless networks, but it  is unable to join the network.  I tried switching off security but that  didn't help either. I have used this card on Windows and it works fine.  


the following messages keeps repeating when trying to join a network.

Appreciate the help.

```
1126.146997] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1126.147008] =================>ieee80211_authentication_req():a   uth->algorithm is 0
[ 1128.640027] Linking with NKX44,channel:1, qos:0, myHT:1, networkHT:0,  mode:6
[ 1128.640034] ===>ieee80211_associate_procedure_wq(), chan:1
[ 1128.678450] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()   Switch to 20MHz bandwidth
[ 1128.678452] 
[ 1128.695663] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1128.695672] =================>ieee80211_authentication_req():a   uth->algorithm is 0
[ 1131.190031] Linking with NKX44,channel:1, qos:0, myHT:1, networkHT:0,  mode:6
[ 1131.190037] ===>ieee80211_associate_procedure_wq(), chan:1
[ 1131.228807] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()   Switch to 20MHz bandwidth
[ 1131.228810] 
[ 1131.243549] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 1131.243557] =================>ieee80211_authentication_req():a   uth->algorithm is 0
```

---

