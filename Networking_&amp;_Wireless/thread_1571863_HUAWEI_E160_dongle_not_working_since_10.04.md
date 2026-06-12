---
title: "HUAWEI E160 dongle not working since 10.04"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by skkeeper on 2010-09-10
Hi there,
I'm running Ubuntu 10.10 beta 1 amd64(but I've been having this problem since 10.04) and I can't seen to make my HUAWEI E160 to work. Before 10.04, everything just worked out of the box, but since 10.04 the dongle shows up in the network manager but just fails to connect (enter infinite loop trying to connect sometimes).

My ISP is Optimus Kanguru in Portugal if that is relevant.

I've compiled usb_modeswitch manually and changed the rules of udev like its described in this topic ([http://ubuntuforums.org/showthread.php?t=1473228](http://ubuntuforums.org/showthread.php?t=1473228)) nothing worked. I even tried to run the sakis3g script, but no luck.

I've been wondering about google and I'll dump here some information I hope its usefull to solve this problem.

lsusb | grep Huawei
Bus 002 Device 011: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

dmesg | grep HUAWEI
[ 59.057641] scsi 10:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 59.060908] scsi 11:0:0:0: Direct-Access HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2
[ 2405.406416] scsi 16:0:0:0: Direct-Access HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2
[ 2405.410738] scsi 15:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 2637.465544] scsi 20:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 2637.468978] scsi 21:0:0:0: Direct-Access HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2
[ 2666.163494] scsi 25:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 2666.165624] scsi 26:0:0:0: Direct-Access HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2

cat /var/log/usb_modeswitch_2-1\:1.0
USB_ModeSwitch log from Tue Sep 07 14:52:28 WEST 2010

Using global config file: /etc/usb_modeswitch.conf
raw args from udev: /2-1:1.0
Bus ID for device not given by udev.
Trying to determine it from kernel name (2-1:1.0) ...
Top sysfs directory not found (/sys/bus/usb/devices/2-1)! Exiting

This is really getting anoying, since I have to come back to Windows everytime I'm out of reach of a wifi spot. Please help if you can.

Thanks & namaste

---

