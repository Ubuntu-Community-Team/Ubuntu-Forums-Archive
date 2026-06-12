---
title: "No wireless in 9.10"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by BramWillemsen on 2009-10-29
Hi all :) 

I just installed 9.10 on my HP 6735s laptop (clean install). In 8.10 and 9.04 I had the ability to detect wireless networks. Right now, when I left click the network icon at the top right of the screen I only see wired connection. Wireless does not show up! I did reboot and I did make sure I switched wireless on with the wireless button on my laptop. 

How should I fix this problem? I really need wireless if I take my laptop to the university library :(

Bram

---

### Post by BramWillemsen on 2009-10-29
lspci -v | less gives:

06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 137d
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 92000000 (64 bits, non-prefetchable) [size=16k]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced error reporting <?>
        Capabilities: [160] Device Serial Number 21-00-89-ff-ff-00-09-6c
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

**--------------------------------------------------------------------**

lshw gives:

*-network
   description: Network controller
   product: BCM4312 802.11b/g
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:06:00.0
   version: 01
   width: 64 bits
   clock: 33MHZ
   capabilities: pm msi pciexpress cap_list
   configuration: driver=b43-pci-bridge latency=0
   resource: irq:17 memory:92000000-92003fff


**--------------------------------------------------------------------**

iwconfig

lo            no wireless extensions

eth0          no wireless extensions

pan0          no wireless extensions

---

### Post by BramWillemsen on 2009-10-29
in System->administration->Network tools 3 Network devices show up.

-Loopback Interface (lo)-
-Ethernet Interface (eth0)      ,card for my UTP connection
-Unknown Interface (pan0)  <-- maybe wireles?

---

### Post by BramWillemsen on 2009-10-29
I guess most people are configuring 9.10 for themselves now

---

### Post by J V on 2009-10-29
This might be too simple, but if you rightclick the icon and tick the wireless checkbox?

---

### Post by BramWillemsen on 2009-10-29
that was the first thing that entered my mind too ;) But there is no tick for wireless.

---

### Post by jperez on 2009-10-29
Well, it shows your card there, but obviously is not loading the driver needed for your wireless card.  Perhaps a search of your driver on the forums might turn up something.  Also, that I know of, some Broadcom wireless cards seem to have restricted hardware drivers for them, so that might be where you need to look under Hardware Drivers.

Jesse~

---

### Post by BramWillemsen on 2009-10-29
Thanks for the suggestions. This post solved it for me though. Kudos to the poster

[http://ubuntuforums.org/showthread.php?p=8189977#post8189977](http://ubuntuforums.org/showthread.php?p=8189977#post8189977)

---

