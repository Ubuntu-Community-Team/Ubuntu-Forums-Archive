---
title: "Wireless &quot;Device not ready&quot;"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Rushuhh on 2010-02-02
My wireless was working fine before but after a reboot it says "device not ready" and I am not able to see networks. Tried "rfkill unblock all", that didn't do anything.

Here are the results of lshw -C network:
```

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 03
       serial: 00:22:69:04:7f:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:ff:98:0c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=half firmware=sb v3.04 ip=168.122.192.58 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:30 memory:f9bf0000-f9bfffff

```

Doesn't show that the wireless is disabled. I'm running out of ideas, help please.
Running Xubuntu 9.10

---

### Post by Rushuhh on 2010-02-02
Bump... Help please

---

### Post by BLoB626 on 2010-02-25
I've got the same problem

---

