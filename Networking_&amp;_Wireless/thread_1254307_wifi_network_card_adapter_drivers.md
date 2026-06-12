---
title: "wifi network card adapter drivers"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by captain22275 on 2009-08-31
i am duel booting ubuntu and vista and vista says my wifi device is a broadacom network adapter but i can't seem to get it to work with ubuntu as i can't find any drivers or ways around it also my pc is a dell inspiron 531 if that helps

---

### Post by gareththered on 2009-08-31
Start by entering the following:-
```
sudo lshw -C network
```This will tell you what all your networking hardware is.

This is an example (my laptop).```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:42:36:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.72 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```You will probably get more output than this, but we're interested in the one that has a description of 'Wireless interface'.  The product line should give you a clue as to what your wifi card is.

---

