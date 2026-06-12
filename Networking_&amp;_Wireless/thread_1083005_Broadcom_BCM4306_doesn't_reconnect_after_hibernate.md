---
title: "Broadcom BCM4306 doesn't reconnect after hibernate"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by rubenverweij on 2009-02-28
Hi everyone,
I have successfully installed my Broadcom BCM4306 wireless card, only it doesn't reconnect after hibernating. This is the output of lshw:
```
*-network:0
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=b43-pci-bridge latency=32 module=ssb

```
The connection information suggests the driver isn't recognized, but it does work properly. (also see the attachment)
I saw under "Edit Connections",  "System setting" is checked. I tried to uncheck that, but the settings don't get updated. Does that have something to do with it?
I hope someone knows a solution!
Ruben
P.S.: I also noticed the full 54 mb/s isn't being used, is that a driver issue?

---

