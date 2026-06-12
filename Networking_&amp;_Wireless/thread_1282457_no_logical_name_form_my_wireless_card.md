---
title: "no logical name form my wireless card"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by MavisCruet on 2009-10-04
Hello,

I am trying to get my girlfriend's desktop configured for linux and wireless.  Never done wireless before.

I have plugged in a Belkin F5D7000 version 2000 and it knows it's there but wants to install a Broadcom driver.  I have installed the belkin driver using ndiswrapper but can't seem to make it attach.

I don't seem to have a logical name for the card.

Output of lshw -C network is below.  Can anyone help, I want to get it wireless and get the ugly blue lump out of the front room!

*-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

---

### Post by kreggz on 2009-10-06
You can install the proprietary BCM driver through hardware drivers to activate that. To launch that from the CLI you can type: jockey

---

