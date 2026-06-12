---
title: "Broadcom Ethernet &amp; Atheros WiFi problems"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by siabost on 2012-02-06
Hi,
Acer Aspire 5733, i3, 4Gb Mem, 500Gb Hard drive.
Ubuntu 11.10 64bit.

I have the following re Wired & Wireless LAN:
```
 *-network 
                description: Ethernet interface 
                product: NetLink BCM57780 Gigabit Ethernet PCIe 
                vendor: Broadcom Corporation 
                physical id: 0 
                bus info: pci@0000:01:00.0 
                logical name: eth0 
                version: 01 
                serial: b8:70:f4:8a:7c:d4 
                size: 10Mbit/s 
                capacity: 1Gbit/s 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=half firmware=sb latency=0 multicast=yes port=MII speed=10Mbit/s 
                resources: irq:43 memory:d3400000-d340ffff 
      
           *-network 
                description: Wireless interface 
                product: AR9285 Wireless Network Adapter (PCI-Express) 
                vendor: Atheros Communications Inc. 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: wlan0 
                version: 01 
                serial: 68:a3:c4:e4:db:77 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-15-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn 
                resources: irq:17 memory:d2400000-d240ffff 
```

I am dual-booting with Win7.

I can't get a wired connection in Ubuntu although the network-manager system icon shows that one has been achieved.
The wireless card connects but tends to disconnect at distances over say 6m and fails to reconnect until I move closer to the router - no such problem in Windows or with my Sony VAIO laptop which has a different wifi card.

I have tried a couple of things - blacklisting the ath9k driver and trying the Win7 driver via ndiswrapper but I just get "Network Unclaimed".

Also created /etc/modprobe.d/ath9k.conf & adding the line:
```
options ath9k nohwcrypt=1
```
which seemed to improve things a bit.

I'm a loss as to what to try next.

I have no idea what to do about the Broadcom ethernet problem either so help for both/either problem would be gratefully received.

Many thanks

---

### Post by siabost on 2012-02-08
Hmmm.

A bit more research has revealed that the MadWiFi driver ath9k may render a weaker signal from the AR9285 wireless chip. Though it possibly doesn't explain why it shows a moderately weak signal but then disconnects.

On another note, the MadWiFi site seems not to have been updated since 2009. This is a recurring problem with driver solutions in Linux - it goes fine for a while but devs have real lives too and end up having to earn a living.

The larger distros should get together to at least maintain these projects once they get started.

I have still no idea what's going on with my wired connection.

Ta.

---

### Post by yuki2012 on 2012-02-09
You should go to the Wifi settings to cheak out

---

