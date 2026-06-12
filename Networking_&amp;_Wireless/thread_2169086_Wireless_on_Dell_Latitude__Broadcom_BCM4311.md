---
title: "Wireless on Dell Latitude / Broadcom BCM4311"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by chris53 on 2013-08-20
Hi guys,

I'm brand new to Ubuntu and trying to get my wireless working with my Dell Lattitude.   I have activated the suggested wireless driver and restarted but I am unable to see any available wireless networks etc..    Any help would be greatly appreciated.    

I ran the command "rfkill list all" and below is what was returned:
0: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no

Then I ran the command "lspci -nn | grep 0280" and below is what was returned:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Any help would be greatly appreciated.  

Thanks,
Chris

---

### Post by chili555 on 2013-08-20
Asked and answered many times; however, please obtain a temporary wired ethernet connection and open a terminal and do:> sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfreeDetach the ethernet, reboot and enjoy your wireless.

---

### Post by chris53 on 2013-08-20
Thank you for your reply but it still does not work.   I have no idea whats going on with this thing..

---

### Post by chili555 on 2013-08-20
Please run and post:```
sudo modprobe b43
dmesg | grep b43
rfkill list all
```Thanks.

---

