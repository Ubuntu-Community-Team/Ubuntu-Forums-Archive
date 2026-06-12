---
title: "Can't get Netgear WN511B to work on 270Mbps"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by hansheijmans on 2009-12-07
Hi folks,

I'm using a WN511B 802.11n wireless network adapter with Ubuntu Karmic, using the latest Broadcom STA driver (which is the only driver I could find for this adapter). So far so good I managed to get it work properly except for the fact that it runs on 802.11g mode (54 Mbps max) while connected to my Netgear WNR834Bv2 (802.11n 270 Mbps).

Does anyone know how to get it working on 270 Mbps? I prefer not to use the ndiswrapper method as in my opinion it's not really "Linux-like", but more or less a Windows-infection in my Ubuntu install.

lspci shows:
> 04:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)lshw:
> 
     *-network
          description: Wireless interface
          product: BCM43XG
          vendor: Broadcom Corporation
          physical id: 1
          bus info: pci@0000:04:00.0
          logical name: eth2
          version: 01
          serial: 00:18:4d:87:5e:3c
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.0.0.3 latency=64 multicast=yes wireless=IEEE 802.11bgn
          resources: irq:19 memory:44000000-44003fffThanks for your help!

---

### Post by hansheijmans on 2009-12-12
Anyone?

---

