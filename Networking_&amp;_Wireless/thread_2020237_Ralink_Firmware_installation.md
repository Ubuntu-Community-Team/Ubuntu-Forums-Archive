---
title: "Ralink Firmware installation"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by zarkony on 2012-07-07
Ok, so I am completely new to linux, so I would love a little bit of help with this. I am running a dual-booting Windows 7/ubuntu 12.04 (both 32 bit) pc, but I can't get the wireless card working with ubuntu. I ran the sudo lshw -C networking command and found the card is a Ralink RT3060. I followed this guide( [http://bit.ly/LVZX2s](http://bit.ly/LVZX2s) ) to install the firmware (drivers are apparently already included in ubuntu). However, the package fails to install, giving this error: 

Unpacking firmware-ralink (from .../firmware-ralink_0.36_all.deb) ...
dpkg: error processing /var/cache/apt/archives/firmware-ralink_0.36_all.deb (--unpack):
 trying to overwrite '/lib/firmware/rt2870.bin', which is also in package linux-firmware 1.79
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/firmware-ralink_0.36_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by xtracool_protik on 2012-08-19
It wouldn't install cause as message said:
> dpkg: error processing /var/cache/apt/archives/firmware-ralink_0.36_all.deb (--unpack):
trying to overwrite '/lib/firmware/rt2870.bin', which is also in package linux-firmware 1.79

You may try installing 
```
 sudo apt-get install linux-firmware-nonfree
```

Or uninstall everything related to linux-firware and then install firmware-ralink

**However I won't recommend it as I don't know what all things are supported by linux-firmware.**

---

