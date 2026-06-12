---
title: "Unknown problem with Broadcom 4727"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by MarsMartianMan on 2012-01-26
I'm running Ubuntu 10.4 LTS on an Acer Aspire one d255e netbook. The netbook has a Broadcom Corporation wireless network controller (Model 4727, rev 01), and I cannot get it to work.

"sudo lshw -c network" outputs (irrelevant information omitted):

```

*-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:56000000-56003fff
```I followed this tutorial to try to get it to work (Actual page is dead, so google cache is all you get): [http://webcache.googleusercontent.com/search?q=cache:ZVzlcyxg7aAJ:www.cnx-software.com/2011/08/21/installing-ubuntu-10-04-lts-in-acer-aspire-one-d255/+&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:ZVzlcyxg7aAJ:www.cnx-software.com/2011/08/21/installing-ubuntu-10-04-lts-in-acer-aspire-one-d255/+&cd=1&hl=en&ct=clnk&gl=us)

However, even after following the tutorial and using the built in "Hardware Drivers" tool, it still won't work. The "sudo lshw -c network" still outputs the same thing, even though the build in Hardware Driver tool says the driver is activated. I honestly don't know what is going on. Can someone point me in the right direction here?

---

