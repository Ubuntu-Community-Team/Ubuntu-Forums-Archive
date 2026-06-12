---
title: "Ad-HOC WIFI"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Yoeri on 2006-06-04
I have a little network between a Windows XP box and an Ubuntu Laptop (dual-booting with XP). Connection between both are either wired or wireless, depending on where i am using the laptop. I am trying to configure Ubuntu to use the Wireless connection (wired works fine). Since I am complete new to linux I'll try and provide as much info as I can get fron the interfaces.

The wireless adapter on the laptop is detected in Ubuntu. It can give me a list of available networks so I guess there is no driver problem. The interface has a Zydas ZD1211 chip on it which is supported.

On the XP-side I disabled all the security stuff and gave the wireless network the ssid "Broken". The network between both pc's is an ad-hoc (peer-to-peer) connection so there is NO accesspoint.

Content of ** /etc/network/interfaces** :
```

iface wlan0 inet dhcp
wireless-essid Broken
auto wlan0
```

When running **sudo ifdown wlan0** i get:
```
Listening on LPF/wlan0/00:13:d4:2e:39:70
Sending on   LPF/wlan0/00:13:d4:2e:39:70
Sending on   Socket/fallback
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Invalid argument.
```

**iwconfig wlan0** gives me:
```
wlan0     802.11b/g NIC  ESSID:"Broken"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=4/92  Signal level=4/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The ESSID is filled in properly, I do notice that the signal strength is "problematic" altough this was neven an issue under the other OS i am running. Do I have to do something "special" since I want to connect ad-hoc instead of via a router ?

Any suggestions ?


Thanks ....

Yoeri

---

### Post by rmjb on 2006-07-05
You can find an ad-hoc wifi command here. It worked for me:
[http://www.ubuntuforums.org/showthread.php?t=205501](http://www.ubuntuforums.org/showthread.php?t=205501)

- rmjb

---

### Post by rmjb on 2006-07-11
You can also check out wifi-radar to get a more powerful configuration gui for your wifi: [http://packages.ubuntu.com/wifi-radar](http://packages.ubuntu.com/wifi-radar)

- rmjb

---

