---
title: "Wireless troubleshooting"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Liliitha on 2009-01-01
Well I am unable to connect to the internet.  This is the information I got from the help section.  Please help.

[QUOTE=Terminal]gaurdian@ubuntu:~sudo lshw -C network
*-network
  description: Network controller
  product: BCM4306 802.11b/g Wireless LAN Controller
  vendor: Broadcom Corporation
  version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32 module=ssb

*-network: 0 Disabled
  description Wireless interface
  physical id:1
  logical name: wlan0
  serial: 00:0c:41:65:7e:a4
  capabilities: Ethernet physical wireless
  configuration: broadcast=yes driver=bridge multicast=yes wireless=IEEE 802.11b/g

*-network: 1 Disabled
  description: Ethernet interface
  physical id= 2
  logical name: pan0
  serial: ee:7e:5d:de:7b:26
  capabilities: Ethernet physical
  configuration: broadcast=yes driver=bridge driverversion=2.3 firmware= N/A link=yes multicast=yes

gaurdian@ubuntu:~$iwconfig
lo[CENTER]no wireless extensions.[/CENTER]
wmaster0[CENTER]no wireless extension[/CENTER]
wlan0[CENTER]IEEE 802.11b/g  ESSID:""
Mode: Managed Frequency: 2.412GHz Acess Point:                           Net-Associated
TX-Power = 0dBm
Retry min limit:7  RTS thr: off Fragment thr: 2352 B
Power Management: off
Link quality: 0 Signal level: 0 Noise level: 0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excess retries:0  Invalid misc:0  Missed beacon:0[/CENTER]
pan0[CENTER]no wireless extensions[/CENTER].[/QUOTE]

It looks as if the wireless wlan0 under network 0 has been disabled but I am unsure if this is correct and unsure how I could fix something like this.

---

### Post by ieee488 on 2009-01-01
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by kevdog on 2009-01-01
Disabled is different than Unclaimed.

What about if you just type
sudo ifconfig wlan0 up

Then I bet it is at least ENABLED

---

### Post by Liliitha on 2009-01-02
> **ieee488 said:**
> [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Well can that error above be solved by the method in this thread?  What is the error above saying, I cannot really read the terminal very well... :(  Is it actually a problem installing my driver because I thought it looked like it was saying the driver was in place and being read.

It says WEP is nonactive so there is no protection on my wireless router.  Should I be seeing the wireless networks in a list somewhere?

---

