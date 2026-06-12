---
title: "Wifi continually disconnecting"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by Inisfad on 2013-04-01
The internet indicates that after the 12.04 upgrade, there is a bug involving the constant dropping of wifi signal by network manager.  I am having this problem as well, where perhaps once an hour, the wifi suddenly drops off, and network manager searches again for the wifi connection.  It will not connect again, unless I turn my modem off and back on, wherein it will either connect again, or ask for my password and connect again.  I cannot see any 'fix' for this on the forum or on the internet.  Does anyone have any information as to whether this bug was fixed, or if there are particular settings needed to avoid this issue?  Thanks.

---

### Post by praseodym on 2013-04-01
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
```
I recommend pure WPA2-AES encryption.

---

### Post by Inisfad on 2013-04-01
Thanks for the reply.   After studying a number of options, I uninstalled network-manager today, and am now using wicd.  So far (fingers crossed) I have had no dropping issues.  This' fix' apparently has worked for some, but not all - hopefully I am one of the lucky ones.  If it resumes dropping out as in the past, I shall post the info you requested.  Thanks again.

---

