---
title: "Inbuilt 3G CDMA EVDO Modem (Qualcomm)  on Haier(Olive) 107 Netbook"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by Hridbijoy on 2013-05-21
I just shifted from windows (XP) to Linux. Though I am liking it very much but unfortunately can't access internet because my netbook has inbuilt 3G Modem . I used to connect to internet through a dialer software (Olive Dialer) on XP but don't know how to connect on Linux. Modem- 3G CDMA EVDOQualcommService porvider- Tata Photon + ( India)

---

### Post by praseodym on 2013-05-21
Please show the outputs of these terminal (CTRL+ALT+T) commands:
```

lsusb
usb-devices
cat /var/lib/NetworkManager/NetworkManager.state
lsmod
rfkill list
ifconfig -a
egrep -i 'net|eth|wlan|firm|reason' /var/log/syslog 
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8|FW' 

```
The last one is a "one-liner" you better copy/paste it ;)

---

