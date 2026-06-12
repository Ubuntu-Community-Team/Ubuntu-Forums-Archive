---
title: "Wireless card not working"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Modplanman on 2009-10-13
Just recently installed Ubuntu 9.04 on a laptop which uses a plugin wireless card.

The card itself is an F5D7011. The card is detected and the driver loaded, but isn't won't enable. Can anyone help?

output of lshw:

```

 *-network
          description: Network controller
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:02:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master
          configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:ed:9e:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg



```Also included is a screenshot of network manager. Note how it shows wireless networks, but no actual networks (even though I do have one available), also showing the card seems to be picked up, but not enabled.

---

