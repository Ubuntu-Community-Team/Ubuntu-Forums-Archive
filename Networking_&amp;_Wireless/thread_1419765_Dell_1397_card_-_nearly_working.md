---
title: "Dell 1397 card - nearly working"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by XmaX on 2010-03-02
I tried the standard drivers, but they didn't work, so I used the ones from Broadcom ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)). I then followed this script:
```
 mkdir hybrid_wl
cd hybrid_wl/
tar xzf home/xmax/downloads/hybrid-portsrc-x86_32-v5.60.48.36.tar.gz 
make
lsmod | grep "b43\|sbb\|wl"
sudo rmmod b43
sudo rmmod ssb
sudo cp wl.ko /lib/modules/2.6.31-14-generic/kernel/net/wireless/
sudo cp wl.o /lib/modules/2.6.31-14-generic/kernel/net/wireless/
sudo modprobe lib80211
sudo insmod wl
sudo insmod wl.ko
```
And it works perfectly.

The problem is, I have to run that on every startup. How to make it more automatic?

---

### Post by chili555 on 2010-03-02
Please try running this:```
sudo apt-get install bcmwl-kernel-source
```Then reboot and let us know if it starts automatically.

---

