---
title: "Can't Get Broadcom or any other drivers working"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by matthewbostic on 2009-06-03
I'm trying to get my drivers to work for either my broadcom pci card or i also have a trend-net usb adapter. I have installed the drivers for both using ndiswrapper both using the GUI and using terminal. The drivers do install but it says that the hardware is not present with both drivers. Another problem is I do not have the option of using wired internet. I'm using a free wifi connection from my neighbor. I think asking to run cat5 might be pushing it. This problem has kept me up at night for hours and I still haven't solved it. I hardly ever post on forums but sought this one as a last resort.

I am using Ubuntu 9.04 (both on my laptop and my desktop the laptop works fine wirelessly I use it to troubleshoot) with a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.  Frankly I'm not very worried about the tend-net usb adapter but it does use the driver, zd1211bu.inf and the model is TEW-429UF.

I have searched these forums for an answer but haven't found anything specific enough for my problem. Also at times, I'm going to sound totally new at this, I was gone for 5 months at Ft, Leonard Wood and have been so out of touch with computers.

---

### Post by matthewbostic on 2009-06-09
Ok so thanks for the help? Anyone?

---

### Post by dmizer on 2009-06-09
Broadcom drivers usually need to get updates from the internet in order to work. Have you tried connecting to the net via a wired internet connection?

If so, please post the output of:
```
lshw -C network
```

---

### Post by superprash2003 on 2009-06-10
here's a useful link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

