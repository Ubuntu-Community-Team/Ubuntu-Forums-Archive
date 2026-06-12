---
title: "Help my wireless is turtle-slow?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Cyberbuddha on 2009-02-12
Hello I just started using Ubuntu and love it allready :P - but ran into some problems with my wireless. The connection is really slow i can maximun dl with 32 kb/s comparing to 600 kb/s when i was using Windows XP?

Please help I am a noob trapped in the Ubuntu-dungeon?

---

### Post by Cyberbuddha on 2009-02-12
*-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wmaster0
       version: 01
       serial: 00:10:60:60:89:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:7e:c4:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:bb:0a:ca:b2:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multica

---

### Post by RavanH on 2009-07-12
Old post but if still relevant: Please check out my fix on [http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785) which involves switching to Wicd plus a small pre-connection script.

Let me know if it works or not :)

---

