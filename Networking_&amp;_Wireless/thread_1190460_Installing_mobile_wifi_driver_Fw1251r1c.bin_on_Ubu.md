---
title: "Installing mobile wifi driver Fw1251r1c.bin on Ubuntu (ARM)"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by nfox on 2009-06-17
I hope this isn't considered too off track, but can anyone help me figure out how to install this driver: fw1251r1c.bin? I'm chrooting Ubuntu on Android and trying to get the wifi driver to load. Worse is that it's not running on a typical Android phone. Since our thread on xda-developers doesn't really touch on Ubuntu specific issues, I'm hoping for any guidance on setting up the driver. Also, this is the ARM port if that matters

In Android, the procedure is:
```
cp /system/etc/wifi/wpa_supplicant.conf /data/misc/wifi/wpa_supplicant.conf
insmod /system/lib/modules/wlan.ko
wlan_loader -f /system/etc/wifi/Fw1251r1c.bin -e /proc/calibration -i /system/etc/wifi/tiwlan.ini
cd /data/local/tmp
wpa_supplicant -f -Dtiwlan0 -itiwlan0 -c/data/misc/wifi/wpa_supplicant.conf &
ifconfig tiwlan0 192.168.1.100 netmask 255.255.255.0
ifconfig tiwlan0 up
```

so how would I even go about this? Thanks for any help

---

### Post by MaindotC on 2009-06-17
I'm not familiar with Android or drivers for mobile phones but I would like to offer what I can on just the basic concept of loading drivers (or in Linux we typically call them modules).  You used the insmod command to load the wlan.ko module.  It appears that that is the module to communicate with the wifi card.  Please post the output of:
```

lshw -C network
lsmod
iwlist scan

```

---

### Post by iTrickU on 2009-07-21
> **nfox said:**
> I hope this isn't considered too off track, but can anyone help me figure out how to install this driver: fw1251r1c.bin? I'm chrooting Ubuntu on Android and trying to get the wifi driver to load. Worse is that it's not running on a typical Android phone. Since our thread on xda-developers doesn't really touch on Ubuntu specific issues, I'm hoping for any guidance on setting up the driver. Also, this is the ARM port if that matters

In Android, the procedure is:
```
cp /system/etc/wifi/wpa_supplicant.conf /data/misc/wifi/wpa_supplicant.conf
insmod /system/lib/modules/wlan.ko
wlan_loader -f /system/etc/wifi/Fw1251r1c.bin -e /proc/calibration -i /system/etc/wifi/tiwlan.ini
cd /data/local/tmp
wpa_supplicant -f -Dtiwlan0 -itiwlan0 -c/data/misc/wifi/wpa_supplicant.conf &
ifconfig tiwlan0 192.168.1.100 netmask 255.255.255.0
ifconfig tiwlan0 up
```

so how would I even go about this? Thanks for any help

These commands need to be run on the phone itself so; go to the android market place, download a terminal emulator and run the commands you need to.

---

### Post by nfox on 2009-07-21
I was hoping that I could bind the interface to the chroot and ignore the fact that the driver is being rejected in Android.

---

