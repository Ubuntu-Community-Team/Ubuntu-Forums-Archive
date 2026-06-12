---
title: "Not able to connect to Wireless"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by Moofknock on 2010-08-19
Ok... I'm a first time Ubuntu user and I just installled it more out of curiosity than anything else so I don't know jack abiut linux just that people say it's better.
 
Anyway I have a Dell Inspiron 1526 laptop and I'm unable to connect to the wireless network. The router that we use is an Apple Airport Express device to connect. 
 
I checked using the troubleshooting guide and this is what I got in the Terminal:
 
 
moofknock@moofknock-laptop:~$ sudo lshw -C network
[sudo] password for moofknock: 
*-network 
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:fe8fc000-fe8fffff
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 7
bus info: pci@0000:03:07.0
logical name: eth0
version: 10
serial: 00:1d:09:36:16:f8
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: irq:20 ioport:ce00(size=256) memory:fe5ff300-fe5ff3ff
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:1f:3a:43:70:f5
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
moofknock@moofknock-laptop:~$ 
 
 
 
I don't have any idea to fix this... HELP!!!!!

---

### Post by grahammechanical on 2010-08-19
I am not an expert but I have just run sudo lshw -C network to compare my set up with your one and the difference is that your wireless interface is marked as disabled. Mine is not marked like that even though my wireless connection is not connected. I am using ethernet at the moment.

All I can think of to help you is to wonder if you have given network manager the router/modem's wireless key, also called WPA-PSK if that is the type of encryption being used. I have found that a password is not necessary if you are using a wired connection but it is necessary if you are connecting by wireless. Otherwise, anybody with wireless in the computer could access your wireless router and connect to the internet using the service that you are paying for.

As I am new to all of this myself I cannot provide the clever solutions. I can only offer the answers that I have learnt. The simple ones.

Regards

---

### Post by varunendra on 2010-08-21
A few quick checks-

[LIST=1]
[*]Make sure the wireless interface is 'switched on' (see if there is any manual switch for it on your laptop).
[*]Right-click on the NetworkManager icon on the panel (3 concentric arcs at the top-left) and make sure 'Enable Networking' is ticked.
[/LIST]
If these are okay, open terminal (Applications>Accessories>Terminal) & try the following command:
```
sudo ifconfig wlan0 up
```
```
sudo dhclient
```

If the above command doesn't help, enter the following commands and post the results here:
```
ifconfig -a
```
```
iwconfig
```
```
sudo dhclient
```

For posting the results, just copy the output in the terminal, paste in your new post, highlight (only) the pasted text and click on the # icon on the editing panel.

---

