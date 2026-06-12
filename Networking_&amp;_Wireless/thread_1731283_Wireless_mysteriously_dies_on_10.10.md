---
title: "Wireless mysteriously dies on 10.10"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by CaptainMorgan08 on 2011-04-17
Hello,

I've had Ubuntu 10.10 installed on this particular machine for almost 6 months now, and haven't had an issues until yesterday.  It no longer detects any wireless networks and behaves as if the switch for the network device has been turned off (which is has not).  I've followed the following troubleshooting guide to no avail.

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

The following is the relevant output of lspci and lshw.

```

$ lspci
...
18:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
...

$ sudo lshw -C network
  *-network
    description: Ethernet interface
    product: 82567 Gigabit Network Connection
    vendor: Intel Corporation
    physical id: 19
    bus info: pci@0000:00:19.0
    logical name: eth0
    version: 03
    serial: 00:17:42:c8:35:37
    capacity: 1GB/s
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
    resources: irq:43 memory:f2700000-f271ffff memory:f2724000-f2724fff ioport:1820(size=32)
  *-network
    description: Network controller
    product: AR928X Wireless Network Adapter (PCI-Express)
    vendor: Atheros Communications Inc.
    physical id: 0
    bus info: pci@0000:18:00.0
    version: 01
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix bus_master cap_list
    configuration: driver=ndiswrapper latency=0
    resources: irq:18 memory:f2500000-f250ffff

$ iwconfig
lo       no wireless extensions.

eth0     no wireless extensions.

```

I should also note that if I boot into windows, everything works as expected.  Any help would be greatly appreciated.

---

