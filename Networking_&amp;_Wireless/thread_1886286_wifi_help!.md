---
title: "wifi help!"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by argoz17 on 2011-11-24
So I bought a usb wifi antenna for my Ubuntu pc, the wifi drivers were made for widows so I switched them over to Ubuntu. So the antenna works, it located my VirginMobile MiFi device, I clicked on the device and it asked for my password, typed in the pass word and it searched....and searched....and searched....and asked for my password again, the searched....and searched....and searched...So I clicked on my web-browser while it was searching. It said not connected and the network searching applit stopped searching and had the red "!" and said not connected.....so whats up here?

---

### Post by praseodym on 2011-11-24
Hi,

please check:

```
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
```

---

