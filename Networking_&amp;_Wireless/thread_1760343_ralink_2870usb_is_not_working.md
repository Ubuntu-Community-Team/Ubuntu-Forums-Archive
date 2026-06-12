---
title: "ralink 2870usb is not working"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by ipfreak on 2011-05-16
hi all:

i am trying to get skylink 802.1n usb wirless adapter working under ubuntu 10.4 lts. 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

well, it seemed to see something at first:

user@host:~$ lshw -C network
WARNING: you should run this program as super-user.
...

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:0a:65:04:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

mlu@PC2-10G:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 10d5:5a08 Uni Class Technology Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


but it failed to connect a wireless lan with no password. so i followed the following links, added new firmware and new *.dat file:

[https://wiki.archlinux.org/index.php/Rt2870](https://wiki.archlinux.org/index.php/Rt2870)
[https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

well, with new .dat file, new firmware (from ralink web site) and reconfigured .dat file. nothing works.

then i followed this link:

[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

it doesn't work either.

i have run out of idea. any help would be greatly appreciated.

---

### Post by chili555 on 2011-05-16
> Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. Please see posts #4 and 8 here: [http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070](http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070)

---

### Post by ipfreak on 2011-05-17
> **chili555 said:**
> Please see posts #4 and 8 here: [http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070](http://ubuntuforums.org/showthread.php?t=1701167&highlight=2070)


i just can't thank you enough...:)

my best regards

---

