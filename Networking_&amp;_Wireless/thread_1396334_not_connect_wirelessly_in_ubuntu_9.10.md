---
title: "not connect wirelessly in ubuntu 9.10"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by firekai04 on 2010-02-01
i am having trouble getting my wireless internet to work on ubuntu 9.10. i just installed today and it works perfectly fine when connected with the cable. i right click the network connection on top and the "enable wireless networking" is not there. only the "enable networking". i have a dell laptop and there is a switch in the front that enables the wireless adapter when i use windows. but on putting the switch into the on position it doesnt turn on, it stays off. i was hoping that someone would be able to help me, i dont want to have use an ethernet cable everytime i use my laptop. any help is appreciated. thanks.



the following code produced this: 

   sudo lshw -C network

description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:21 memory:fc000000-fc003fff



i solved it using  the solution from this thread:
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by amsterdamharu on 2010-02-01
You could try the following sollution (installing native drivers)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Or here for a wrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

