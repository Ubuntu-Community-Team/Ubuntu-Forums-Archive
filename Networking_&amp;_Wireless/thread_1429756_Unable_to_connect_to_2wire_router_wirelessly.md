---
title: "Unable to connect to 2wire router wirelessly"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by jaeilbes on 2010-03-14
Any help please, I upgraded to 9.10 yesterday after using 9.04 for a bit.  Now I don't have wireless access.  I was able to get the proprietary drivers to work for my Broadcom wireless adapter.  However, for some reason, my adapter will not connect to my 2wire wireless router.  Network is detected and appears to be set up correctly, but it will not connect.

---

### Post by efflandt on 2010-03-14
For some reason when I initially set up wireless in Network Connections, sometimes security settings do not stick or something else does not work until I edit and resave the connection.  Your default WEP key is in square brackets [ ] on your modem/router label, unless you changed it.  I once had a wrong digit trying to read it in the dark.

Make sure that you have it set to "Connect automatically", and "Available to all users".

You didn't say which Broadcom device you have, but some like BCM4311 or BCM4312 use Broadcom STA, while others may need Broadcom B43 activated instead.

---

### Post by jaeilbes on 2010-03-14
BCM4312, verified key multiple times.  Connect automatically and available to all users checked.  STA driver intact.

 *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:e1:b3:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fe7fc000-fe7fffff

---

