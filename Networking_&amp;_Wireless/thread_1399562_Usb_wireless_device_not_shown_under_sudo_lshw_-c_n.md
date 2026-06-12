---
title: "Usb wireless device not shown under sudo lshw -c network"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by thatguy256 on 2010-02-05
Okay currently I am using a a Belkin F6D4050v1 usb wireless n card on a 32 bit intall of ubuntu 9.10.  I have already installed ndiswrapper and installed the the rt2870.inf driver and rebooted. But i still have no wireless.  when I use the command 
 
"sudo lshw -C network"  all i see is my pci wired nic card
 
"lsusb" the ID of the card is "050d:935a Belkin Components"
 
"sudo iwconfig" says
lo  no wireless extensions
etho  no wireless extensions

---

### Post by thatguy256 on 2010-02-05
Currently this is exactly what i am getting out of the terminal
 
```
 
jonathan@desktop1:~$ sudo lshw -C network
[sudo] password for jonathan: 
*-network 
description: Ethernet interface
product: 82801G (ICH7 Family) LAN Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 01
serial: 00:17:31:e9:9c:85
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:20 memory:fdefe000-fdefefff ioport:ee00(size=64)
jonathan@desktop1:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jonathan@desktop1:~$ sudo iwconfig
lo no wireless extensions.
eth0 no wireless extensions.

```
and here is a screenshot of ndisgtk

---

### Post by bkratz on 2010-02-06
Hopefully you can find something useful here

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=050d:935a](http://ubuntuforums.org/showthread.php?t=1342593&highlight=050d:935a)

---

