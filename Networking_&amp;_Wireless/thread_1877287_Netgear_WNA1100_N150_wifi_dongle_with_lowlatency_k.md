---
title: "Netgear WNA1100 N150 wifi dongle with lowlatency kernel"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by christophski on 2011-11-07
Hi, I have a WNA1100 which I have been using fine on 11.10 but recently I started using Abogani's lowlatency kernel as I am doing pro-audio work. However, now ubuntu does not recognise my wifi dongle (though it does show up in lsusb), the light does not shine on the dongle and I cannot select wireless networks. How can I get it working again? Is there a way to tell if the kernel was compiled with support for this network adapter?

Output of lsusb is as follows:
Bus 002 Device 005: ID 0846:9030 NetGear, Inc.

---

### Post by christophski on 2011-11-11
Just discovered this in kern.log, does this provide any insight in to the problem? 

Nov 11 19:53:18 christies-desktop kernel: [15775.563797] usb 2-6: new high speed USB device number 16 using ehci_hcd
Nov 11 19:53:19 christies-desktop kernel: [15775.701250] usb 2-6: ath9k_htc: Firmware - htc_9271.fw not found
Nov 11 19:53:19 christies-desktop kernel: [15775.701273] ath9k_htc: probe of 2-6:1.0 failed with error -22

---

### Post by praseodym on 2011-11-11
Hi,

install the firmware with:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2640681/ath_htc_firmware-1-1.tar.gz
sudo tar xvf ath_htc_firmware-1-1.tar.gz -C /lib/firmware 
```

---

