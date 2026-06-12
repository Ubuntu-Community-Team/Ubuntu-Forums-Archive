---
title: "Wirless not working"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Ducatiboy Stu on 2009-08-25
My wireless does not come up in the network connections list, and I am wanting to get it set up..

```
ncts@ncts:~$ sudo lshw -C network
[sudo] password for ncts: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a3:87:4b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.104 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
ncts@ncts:~$ iwconfig wlan0
wlan0     No such device

ncts@ncts:~$ iwconfig wlan1
wlan1     No such device

ncts@ncts:~$ 

```

Any one got any ideas..??

---

### Post by superprash2003 on 2009-08-26
take a look at this [http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)

---

### Post by Ducatiboy Stu on 2009-08-26
Unfortunatly that didnt help :(

```
ncts@ncts:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ncts@ncts:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ncts@ncts:~$ sudo modprobe pbe5 radio=1

```

---

