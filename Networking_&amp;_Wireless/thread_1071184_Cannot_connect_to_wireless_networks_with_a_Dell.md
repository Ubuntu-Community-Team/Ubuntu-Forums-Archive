---
title: "Cannot connect to wireless networks with a Dell"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Merk2 on 2009-02-15
Hi,

I'm using a Dell Inspiron 1720 and ubuntu 8.10 (with Wubi), and I cannot connect to my wireless network. I can connect to the internet with a wired connection, but I want to figure out how to connect even without a direct connection.

This is the result of "sudo lshw -C network":

```
*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:1b:1a:af
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8d:4f:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.7 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:8e:77:5d:68:3a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I also have the "Broadcom STA wireless driver" activated.

Thanks in advance for any help!

Edit: I should also mention that as this is running off of Wubi, I also sometimes boot in Windows Vista, where I can connect to wireless networks just fine.

---

### Post by unixeducation on 2009-02-15
You may find this link from the Broadcom site helpful: [http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php)

You will need to compile the driver and install it.

---

### Post by Merk2 on 2009-02-15
> **unixeducation said:**
> You may find this link from the Broadcom site helpful: [http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php)

You will need to compile the driver and install it.

Thanks!

I apologize, but I'm pretty new to ubuntu (and linux in general); how do I compile/install the driver? Should I extract the archive?

---

