---
title: "Wireless suddenly not working on Ubuntu 12.04"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by abcex on 2013-07-18
I am having a X220 laptop. Usually I use the ethernet haven't used the wireless for a while but it worked well previously. This morning I try to use the wireless and strange things happen. At first I was able to connect to it, but then when I disconnected and reconnected it, it kept asking for my password for a few times before it can connect, and finally now I cannot connect to the wireless no matter how many times I entered my password. I've verified that the wifi is working on my Windows partition and also on my phone. Does anyone know how to solve this problem?

Here is the output from sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:63:40:07
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-3 ip=165.91.233.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f2500000-f251ffff memory:f252b000-f252bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a0:88:b4:2b:ff:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-36-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f2400000-f2401fff

Any help is greatly appreciated.

---

### Post by praseodym on 2013-07-18
Deactivate the N-mode of the driver (bug)

```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

