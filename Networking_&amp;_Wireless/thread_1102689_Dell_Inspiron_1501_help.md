---
title: "Dell Inspiron 1501 help"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by g33k456 on 2009-03-21
I have a dell inspiron with ubuntu 8.10 installed (I dual boot it and vista). And it won't run the built in wireless card. Please help.

While on ubuntu I have NO internet access so I have to boot up Vista to get on the internet so anything that involves me accessing the internet I better be able to do from vista and move the files to ubuntu.


Thanks for your help,
g33k456


EDIT: This is what happens when I try using the troubleshooter thingy...
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:b6:fc:02
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:d9:6c:19:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 96:fd:82:b6:4f:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
adam@adam-laptop:~$ 

(Yes I am a TOTAL Linux noob)

---

### Post by mringer on 2009-03-22
Everybody has problems with these **blesssed** Broadcom cards. Please try

sudo lshw -C network

If the wireless card is listed UNCLAIMED  then you need to find a device driver. ndiswrapper worked for me, ref:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)

Please understand that I am no sort of expert. If this fails I cannot
give further help.

---

### Post by benmoran on 2009-03-22
I have the same laptop. 

Go to System, Hardware Drivers
and activate the Broadcom restricted driver. I believe it needs to download the firmware though, so you need to plug it directly into your router. Personally I have a cheap $10 wifi dongle that I plug in after a fresh install in order to get it going. 
Good luck!

---

### Post by deviant78 on 2009-03-22
I have the same laptop, best way I found was to connect with a LAN cable and run update manager till system is up to date.

Reboot and go to System, Hardware Drivers.  
If you're running Ubuntu 8.10, enable the "Broadcom STA wireless driver"
While there enable the ATI driver too if it isnt already selected.
Shutdown, remove the cable.
It should be working next time you boot.

---

### Post by g33k456 on 2009-03-22
> **mringer said:**
> Everybody has problems with these **blesssed** Broadcom cards. Please try

sudo lshw -C network

If the wireless card is listed UNCLAIMED  then you need to find a device driver. ndiswrapper worked for me, ref:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)

Please understand that I am no sort of expert. If this fails I cannot
give further help.


Yea I did it is "DISABLED" so that won't work lol...

Anyway thanks for all your help I will see what I can do

---

