---
title: "Wireless Disconnection Every Few Minutes"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by Blurred Talon on 2012-09-30
I've got a Dell Studio 1735 running Ubuntu 12.04 LTS, drivers are up to date.

My wireless is constantly disconnecting on me. I can get it to come back by flipping the switch on my laptop or closing the lid and opening then logging back in.

Some help in fixing this? It's very annoying.

---

### Post by uncaspi on 2012-09-30
Will you please post the content of this command.

sudo lshw -C network

---

### Post by Blurred Talon on 2012-09-30
Here you go.

```
PCI (sysfs)  

  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:ba:f7:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.2.13 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:76:d4:fd
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:f69f0000-f69fffff


```

---

### Post by uncaspi on 2012-09-30
You should go to broadcom website and download the latest driver.

---

