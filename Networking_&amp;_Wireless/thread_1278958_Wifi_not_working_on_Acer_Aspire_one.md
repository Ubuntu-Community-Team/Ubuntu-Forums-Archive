---
title: "Wifi not working on Acer Aspire one"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by SubT on 2009-09-30
Not sure of the model number here, theres one on a white sticker saying 'AO531h-0Bk' and another under an acer logo saying it's ZG8.

wireless card is:
Atheros communications inc. AR9285 Wireless Network Adapter (PCI Express) (rev 01)

When I run **lshw -C network** in a terminal the output is, 
```

WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: L1e Gigabit Ethernet Adapter
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: b0
serial: 00:26:9e:38:c6:6d
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e ip=192.168.1.14 latency=0 module=atl1e multicast=yes
*-network UNCLAIMED
description: Network controller
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: e6:cb:ea:df:04:93
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

Don't seem to be able to get wireless to work, I've tried ath5k, ndiswrapper and madwifi, beginning to think it's just not going to work, any ideas?

---

### Post by t0mppa on 2009-09-30
You have to use ath9k, the other drivers don't support this chip (AR9285). You can get it by either installing the backports (**sudo apt-get install linux-backports-modules-jaunty** or through Synaptic) or the [compat-wireless]("http://linuxwireless.org/en/users/Download") that has to compiled manually. After that you'll also have to manually load the module with **sudo modprobe ath9k** and blacklist and unload any other drivers you've tried.

---

### Post by chili555 on 2009-09-30
I believe this is supposed to work with ath[COLOR="Red"]9[/COLOR]k. It can be found in the package *linux-backports-modules-jaunty-generic* and the other packages it pulls in. 

Incidentally, Network Manager will not allow two connections at once, so once you get the packages downloaded and installed, detach the ethernet cable and do:```
sudo modprobe ath9k
```See if your wireless have come to life with:```
iwconfig
```If you have a new wireless interface, then click the Network Manager icon and see if you can connect.

---

### Post by SubT on 2009-09-30
Worked great, thanks a lot.

---

