---
title: "wifi card as hotspot problem"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by kipelovets on 2010-10-05
hi

i'm trying to get my notebook to work as a wifi hotspot. with my previous ISP i've made it successfully with NetworkManager. but my current ISP requires a pppoe connection (that i made with pppoeconf), and wifi guests don't get connected to the internet. 

i tried to disable NetworkManager and configure it manually but failed :( :

```

phantom@phantom-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
phantom@phantom-laptop:~$ sudo iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

is it possible to bridge pppoe ISP connection and wifi network with NetworkManager? what is wrong with iwconfig if it fails to set Master mode on wlan0 (somehow it should be supported as it works with NetworkManager) ?

---

