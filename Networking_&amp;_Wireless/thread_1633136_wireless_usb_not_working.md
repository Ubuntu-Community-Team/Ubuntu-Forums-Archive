---
title: "wireless usb not working"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by thenetminder33 on 2010-11-28
Hello I  just installed ubuntu 10.04.1 on my pc and i cant seem to get wireless to work...
My wireless card is a TP-Link WN321G usb card.
After looking at other posts and the ndiswrapper wiki I used ndswrapper to install what appeared to be the correct driver from my cd...
ndiswrapper said that the install was successful and that the hardware is present.
However i still cannot connect to any network,

Also if it is helpful:
```
sudo iwconfig wlan1
```
returns
```

wlan1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

```

---

### Post by uncaspi on 2010-11-29
we'll first try to figure out which chipset the beast is using. Please post
lsusb and dmesg | grep controller

---

### Post by thenetminder33 on 2010-11-29
I just booted up into ubuntu... and it connect automatically to my wifi network... maybe ndiswrapper just needed a restart... idk but im happy

Thanks for the help

---

