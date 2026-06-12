---
title: "Lenovo S10-3s Wireless Suspend/Hibernate Issue Fix Found!"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by DieseL1988 on 2011-01-11
If you are having issues with wireless being disabled on startup and having to manually enable wireless; and are also having issues with wireless becoming disabled and broken after a suspend/hibernante;

Add the following to the bottom of /etc/modprobe.d/blacklist.conf
```
blacklist acer-wmi
```

As a little extra, if you are experiencing poor performance from the STA wireless driver while running on battery you can execute the following command
```
sudo iwconfig eth1 power off
```

If you find this improves performance you can make it permanent by adding the following to the bottom of /etc/network/interfaces
```
wireless-power off
```
EDIT: This doesn't appear to work completely as unplugging the AC power resets the wireless power management. a more permanent solution can be found here: [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

Reboot and you should be good to go.

---

### Post by cerosilva on 2011-04-09
I'm gonna try this out. 

Hope it works.... working without wireless is like being chained to the dog house

---

