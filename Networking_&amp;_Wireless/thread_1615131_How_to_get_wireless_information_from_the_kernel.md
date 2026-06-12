---
title: "How to get wireless information from the kernel?"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by mooserider2 on 2010-11-06
How can I get information similar to proc/net/wireless but for more than just the wireless router I'm connected to. I know there has to be a way because when I'm disconnected from all routers the network manager shows signal strength of all available routers.

---

### Post by chili555 on 2010-11-06
How about this?```
sudo iwlist wlan0 scan
```Substitute your interface if it's not wlan0.

---

### Post by DirtyPC on 2010-11-06
Try **ifconfig** also, don't forget if you have want wireless card/usb details.

lsusb/lspci

---

### Post by mooserider2 on 2010-11-06
iwlist is perfect thank you
:guitar: u rock

---

