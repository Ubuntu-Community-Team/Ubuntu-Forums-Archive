---
title: "Unable to use TL-WN821N"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by udiw on 2011-03-03
Hi,

I got a TP-LINK USB wireless module - TL-WN821N, using Ubuntu 10.4 (same problems were also seen in 10.10).

From everything I've read online, the usb should work just fine, since the Atheros ar9170 is built into the kernel. However, when I plug it in, it is detected as a USB device, but there is no wlan associated with it, and basically - nothing happens.

Am I doing something wrong? what should I do so that the Atheros driver is associated with this device?

btw, on Windows it works fine (with the drivers).

Some logs:
```
$ uname -mr
2.6.32-28-generic i686

$ lsb_release -d
Description:	Ubuntu 10.04.2 LTS

$ lsusb
... (trimmed)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsmod |grep ar9
ar9170usb              51296  0 
ath                     7611  1 ar9170usb
mac80211              205402  3 ar9170usb,iwl3945,iwlcore
cfg80211              126528  5 ar9170usb,ath,iwl3945,iwlcore,mac80211
led_class               2864  4 ar9170usb,iwl3945,iwlcore,sdhci


```

---

### Post by chili555 on 2011-03-03
It probably is missing firmware. You can confirm it with:```
dmesg | grep ar9
```If that's the case, get an internet connection and do:```
sudo apt-get install linux-firmware
```Remove and reinsert the device and you should be all set.

Incidentally, Network Manager may have a bit of trouble connecting your Atheros but not your Intel.

---

### Post by masque7 on 2011-07-14
I have solved the problem in this thread:
[http://ubuntuforums.org/showthread.php?p=11046879#post11046879](http://ubuntuforums.org/showthread.php?p=11046879#post11046879)

---

### Post by zombiedude on 2012-01-25
I got the TL-WN821N v2 [Atheros AR9001U-(2)NG] to work on Natty 11.04 (kernel version 2.6.38-8-generic) using the following:

Open a terminal and type

echo "blacklist ar9170usb" | sudo tee /etc/modprobe.d/blacklist-ar9170.conf

and then reboot

see comments 12 & 13 here for more details - [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/495562](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/495562)

Cheers

Zombiedude

---

