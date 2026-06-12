---
title: "Network manager stop working completly (( not working after reinstalling))"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by alieblice on 2011-10-18
HI

ubuntu 11.10 --- sony\vaio f13u 

my network manager was unable to connect to pppoe ((adsl connection)) so i tried to connect with command pppoeconf and it was successful

after two days my wireles lamp didn't turned on and  i did a reboot after that my network manager stop working completely

i reinstalled it but nothing changed

i fined way in internet wich was Not working :

$ rm /var/lib/NetworkManager/NetworkManager.state

if any more data needed please give me the command to i copy\past the out put

---

### Post by alieblice on 2011-10-20
[B]at least help me to solve the wireless problem 
i could connect to adsl by pppoeconf[/B]

---

### Post by dineshs on 2011-10-21
Pl run and post the output of ```
sudo lshw -C network
```

---

### Post by alieblice on 2012-03-31
HI
after all tease days i thought maybe this time i could make it working.

bu now i could connect to wireless and Ethernet  but i cant connect to adsl ? and after making adsl connection ,they doesn't com to list of connection to i could click on them to connect .


```
 sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:b5:a9:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:e8e00000-e8e0ffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: f0:bf:97:1a:f7:e9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:e6620000-e6623fff ioport:a000(size=256) memory:e6600000-e661ffff

```

---

