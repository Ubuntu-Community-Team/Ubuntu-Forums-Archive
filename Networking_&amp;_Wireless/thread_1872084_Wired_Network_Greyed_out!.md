---
title: "Wired Network Greyed out!"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Spetsnaz on 2011-10-30
So Today I was trying to install ISPConfig 3 with a tutorial but I think it made me mess up my settings! 

So now the only way to connect to the internet is wireless
my Wired Network on the top of my screen is all greyed out, so I have spent over 5 hours searching for solutions and help but nothing I hope I could get some help on this.


sudo iptables -L  :

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@spetsnaz:~#  lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:0e:a9:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.79 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:fbef0000-fbefffff
  *-network
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:25:64:ec:29:4b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb ip=192.168.1.85 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:fbff0000-fbffffff
```

---

### Post by Spetsnaz on 2011-10-30
Kinda fixed it
The new Ubuntu is a PIECE OF CRAP!

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
Thanks to that I can use Ethernet and not WIRELESS!

---

