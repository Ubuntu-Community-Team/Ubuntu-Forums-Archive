---
title: "is my PCI Express card enabled?"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by jseagle on 2009-11-07
I'm trying to find out if my PCI Exprees card slot is even enabled...

[http://pastie.org/688268](http://pastie.org/688268) 
 
^^my computer specs^^

---

### Post by chili555 on 2009-11-07
Your question is not very clear to me. Are you asking if your Intel 3945 wireless is enabled? It's hard to tell from the little information you pasted. It may not be working because it's disabled in the BIOS (doubtful), or because the kill switch is nudged over to 'off' (very possible) or because the right driver is not loaded (possible).

Let's check the switch. Please manipulate the physical switch and see if you can get the LED to flicker or light up. Open a terminal and do:```
sudo lshw -C network
```If you see DISABLED opposite your wireless hardware listing, that's a pretty reliable indicator that the switch is off. Is there a driver associated with it, iwl3945, perhaps?

---

### Post by jseagle on 2009-11-07
My onboard wireless works fine, what I am trying to do is use a mobile broadband card with ndiswrapper to use the 'net my mobile broadband card plugs in via PCI Express slot

---

### Post by jseagle on 2009-11-07
jimbo@Jimbo-0001:~$ sudo lshw -C network
[sudo] password for jimbo: 
Sorry, try again.
[sudo] password for jimbo: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:12:73:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:efdff000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8b:32:7d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
jimbo@Jimbo-0001:~$

---

### Post by chili555 on 2009-11-07
> my mobile broadband card plugs in via PCI Express slotWith it plugged in, let's look at:```
lspci -v
```Thanks.

---

### Post by jseagle on 2009-11-07
It'll have to wait until I get home I got a call from work so i won't be able to get back with you until tomorrow

---

