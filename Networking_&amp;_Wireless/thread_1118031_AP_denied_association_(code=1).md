---
title: "AP denied association (code=1)"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by gleble on 2009-04-06
I have just bought a new machine and am trying to get to get the wireless working but dmesg gives me
```
[ 1149.674861] wlan0: AP denied association (code=1)
```
Does anyone know what this means or how to fix it

---

### Post by gleble on 2009-04-07
I am using Intrepid on an Acer 5735 using an Orange Livebox

Here is the result of  sudo lshw -C network in case it inspires ideas. You can see that wlan0 is not disabled??

```
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:e8:e1:26
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.135 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:74:69:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:29:1b:fd:de:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by gleble on 2009-04-08
Tried once more pressing the button on the Livebox and everythings fine. Had to be coz I was sure the config was right

---

