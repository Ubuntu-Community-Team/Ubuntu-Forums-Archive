---
title: "Tips for wireless - maybe add to sticky page:"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by michaelcole1 on 2010-06-23
1) Spend several hours trying to debug disabled wireless through crazy forums and posts.
Solution: Right-click Network Manager -> Enable Wireless

2) Helpful script for getting wireless debug info:
```
#! /bin/bash
# This script will find the needed information for
# wireless troubleshooting.
# Name this file WirelessSetup

go () {
echo " "
echo "===================================="
echo $*
echo "------------------------------------"
echo " "
# redirect stderr to stdout (so error messages can be logged) with 2>&1
$* 2>&1
}

go uname -mr
go sudo lsb_release -d
go lspci -knn
go lsusb
go lsmod
go dmesg | grep firmware
go ifconfig
go iwconfig
go iwconfig wlan0
go iwconfig wlan1
go iwlist wlan0 scan
go iwlist wlan1 scan
go sudo lshw -C network
go sudo /etc/init.d/networking restart
```

Thanks to everyone who helps forums!  You guys are great!

---

### Post by MartinHansell on 2010-06-23
Hi,

Earlier today I posted [this request for help]("http://ubuntuforums.org/showthread.php?p=9498775#post9498775"), and it looks similar to yours...  Did you resolve your problem?  Do you have any ideas about what I can do?

I have attached a file with the output of your script.

Many thanks.

---

