---
title: "KEEBOX Wireless-N USB Adapter 14B2:3C2C"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by FourM on 2011-07-25
It seems an OP abandoned his thread but he was able to successfully able to get his KEEBOX Wireless-N USB Adapter 14B2:3C2C to work using these instructions:

Create a udev rules file:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```
Add this line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="14b2", ATTR{idProduct}=="3c2c", RUN+="/sbin/modprobe -qba rt2870sta"
```
Create a modprobe.d conf file:
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
Add this line:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "14b2 3c2c" > /sys/bus/usb/drivers/rt2870/new_id
```
And finally run:
```
sudo modprobe rt2870sta
```
Or just unplug then replug the adapter.

This was done on Ubuntu 11.04

---

### Post by fishcadet on 2011-10-31
I did this and it worked, but after upgrading to 11.10, it no longer works.  I don't know what I'm missing.  It's very frustrating.

---

### Post by pdc on 2011-10-31
don't you just hate it when that happens?

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by wildmanne39 on 2011-11-01
I did some research and that driver was replaced by rt2800usb, you may need to get rid of that configuration file you altered if it is still present in 11.10.

Then try 
```
sudo modprobe rt2800usb
```
then unplug your wired connection and see if it comes to life if not post the results of:
```
lsmod
```
Thank you

---

### Post by fishcadet on 2011-11-01
[wildmanne39]("http://ubuntuforums.org/member.php?u=508533");  You're the best around.  
It worked.  Thank you very much.

---

### Post by wildmanne39 on 2011-11-01
Hi, your welcome! glad to help.
Enjoy

---

