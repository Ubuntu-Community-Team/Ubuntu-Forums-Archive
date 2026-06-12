---
title: "enuwi-n maybe any ralink driver"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by liljetw on 2009-11-04
they seem to have added updated drivers and didn't blacklist the old ones.
to blacklist the old drivers for ralink only.

Enter this in a terminal and enter your password

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Add these two lines

```
blacklist rt2800usb
```

save exit and reboot

---

### Post by trilobit on 2009-11-04
I have old D-Link DWL-510 2.4GHz Wireless PCI Adapter with ndiswrapper and NET8180.INF file.

After upgrade Jaunty Jackalope to Karmic Koala I have to modify blacklist.conf to make wlan work

gksu gedit /etc/modprobe.d/blacklist.conf
blacklist r818x

Wlan started to work immediately after save file!

---

### Post by henryhmo on 2009-11-05
I tried, but still can't work.  After backlist that ralink driver, the green light even does not flash and no wireless network is detected.
Probably because my Xubuntu Karmic does not carry such a wrapped up driver.  Can you check what driver you are using and I can install it by apt-get?  Thank you!

---

### Post by liljetw on 2009-11-10
I use rt2860 chipset
try removing blacklist rt2870sta
using the commands I listed and reboot

---

### Post by liljetw on 2009-11-10
It worked for me

---

