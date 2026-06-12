---
title: "Unable to connect to network"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by mutonchops on 2009-07-03
Hi,

I have just installed Jaunty (changing from XP) and after several problems getting my wireless card working (a broadcom) and it finally worked after having problems with the ndsiwrapper and using the B43-fwcutter... for about 30 minutes. After a restart my comp tried to connect to my network, however, it just would not connect. The prompting for the network key pops up every couple of minutes, however, I will not connect. Any ideas as to why this is? I'm a complete noob to ubuntu, so please be patient if I seem like an idiot!

This is my lshw info:

*-network
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:0a:05.0
                logical name: wlan0
                version: 02
                serial: 00:16:cf:ad:d4:70
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,12/22/2004, 3.100. latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Thanks

---

### Post by superprash2003 on 2009-07-03
try system->admin->hardware drivers first , if that doesnt work try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

