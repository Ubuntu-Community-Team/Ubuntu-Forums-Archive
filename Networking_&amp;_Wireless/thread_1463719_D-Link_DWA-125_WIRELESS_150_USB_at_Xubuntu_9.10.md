---
title: "D-Link DWA-125 WIRELESS 150 USB at Xubuntu 9.10"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by dginz on 2010-04-27
I got an D-Link DWA-150 USB WiFi-adapter.
I have Xubuntu 9.10

Then I will describe situation in steps:
1) WTF?! System doesn't "feel" it.
  #lsmod | grep rt
It shows modules like **rt2???*** (I don't really remember, what it specifically was, but it doesn't matter), but the real module for my device is **rt3070sta**.
2) Blacklist old modules:
  Add to /etc/modprobe.d/blacklist.conf this lines:
    blacklist rt2x00usb
    blacklist rt2x00lib
    blacklist rt2800usb
    blacklist rt2870sta
3) I downloaded driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2).
  #tar xvf <archive>
  #cd <folder>
  #vim os/linux/usb_main_dev.c
  Add line:
    MODULE_LICENSE ("GPL");
  #sudo make
  #sudo make install
  #sudo reboot
  #sudo modprobe rt3070sta
  #iwlist ra0 scan
    ra0     No scan results
WTF?! :confused:

---

### Post by labinnsw on 2010-04-29
D-Link adapters come with a CD. The drivers are on the CD.

Copy the driver to your system.
[Install ndiswrapper, ndisgtk and ndiswrapper-utils-* from the repositories.]("http://www.youtube.com/watch?v=DZLEZRgWIOc")
Configure ndiswrapper to use the driver you copied.

---

### Post by dginz on 2010-04-29
But maybe it's better to use the native drivers?:)

---

### Post by chili555 on 2010-04-29
Is the behavior improved if you blacklist rt3070sta and un-blacklist rt2870sta and then reboot?

---

### Post by labinnsw on 2010-04-30
> **dginz said:**
> But maybe it's better to use the native drivers?:) May be, I don't know. I thought you just wanted it to work.

---

