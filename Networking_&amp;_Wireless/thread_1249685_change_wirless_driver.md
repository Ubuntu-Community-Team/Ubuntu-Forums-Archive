---
title: "change wirless driver"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by jojom271 on 2009-08-25
1. how do i find out what chipset i have to change my wirless driver.
2. do i have other options on what driver i can use. other than the originall.
problem i feel it is not connecting correctly 
is ther a way to find out if i have the best one for my computer.

computer: toshiba sat m305 s 49052  32/64 4gib using ubuntu64

---

### Post by chili555 on 2009-08-25
> how do i find out what chipset i haveOpen a terminal and do:```
sudo lshw -C network
```You will get information about both your wired ethernet and wireless. It should be clear which is which. Here is the wireless part from mine as an example. It shows the chipset and driver:> *-network
       description: Wireless interface
       product: [COLOR="Red"]PRO/Wireless 3945ABG[/COLOR] [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.108 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg> 2. do i have other options on what driver i can use. other than the originall.
problem i feel it is not connecting correctlyCertainly. There is generally an alternate driver available for everything; some better, some worse.

Before you undertake an arduous process that may or may not inprove your performance, how about telling Dr. Chili what's going wrong. Maybe we can fix it.

---

### Post by jojom271 on 2009-08-25
jojom271@jojom271-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:54:ac:07
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:ba:88:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.190.154 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:61:6c:47:c9:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jojom271@jojom271-laptop:~$

---

### Post by jojom271 on 2009-08-25
i feel that it is working to slow
not connecting well with wirless signal

---

### Post by chili555 on 2009-08-25
How about letting us see:```
iwconfig wlan0
```Thanks.

---

