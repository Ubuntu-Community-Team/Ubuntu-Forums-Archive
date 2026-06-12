---
title: "IBM T60 / Intel 3945 wireless not working"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by tpuller123 on 2013-03-19
I just installed Ubuntu 10.04 LTS on my IBM T60 and I have no wireless. When I use an ethernet cable it works fine, but no wireless. In the drop down menu at the top of the screen, under wireless networks it say "disconnected"

Here is the output from the command sudo lshw -c network:

```
richard@LINUXCNC:~$ sudo lshw -c network
[sudo] password for richard: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:30:f6:92
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:13:02:ba:9d:16
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:edf00000-edf00fff

```
I have seen other people with similar problems but I have not come across a fix for it. If anyone knows of one, it would be appreciated if you could share. It kinda sucks having to be tied to the router with a 15' ethernet cable.

Thanks,
Richard

---

### Post by chili555 on 2013-03-20
An IBM T60 with the Intel 3945 wireless card, eh? I have and use one daily! The first thing I'd check is the wireless switch on the front. [http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg](http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg)

---

### Post by mörgæs on 2013-03-20
Slightly off topic: You should begin with a clean install of 12.04 or 12.10 as 10.04 is soon running out of support.

---

