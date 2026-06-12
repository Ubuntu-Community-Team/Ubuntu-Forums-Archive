---
title: "Problems with wired conection ubuntu 10.04"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by mamamama on 2010-09-14
Hi, I've just installed ubuntu 10.04 in my notebook, and it is working perfeclty, except for the wired connection. I connect my internet cablem but ubuntu does not recognizes it. The message that appears is "no network devices available". So, I've written "sudo lshw -C network", and what appeared is:

network UNCLAIMED
description: Ethernet controller
product: AR8151 v1.0 Gigabit Ethernet
vendor: Atheros Communications
phisical id: 0
bus info: pci@0000:01:00.0
version: c0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0
resources: memory:d34000000-d343ffff ioport:2000(size=128) 

network UNCLAIMED
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
phisical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:d2400000-d2403fff

Someone can help me, please! (I'm a beginner: I've tried to read old posts, but I could not find a solution for my problem!)
Thanks a lot!

---

### Post by blakep2 on 2010-09-15
Can you connect to the internet at all on the machine.  Foe example through wireless.  If so go to System > Administration > Hardware Drivers.  See if the card is listed here.  If so enable it.

---

### Post by dineshs on 2010-09-15
Have you seen this?
[http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential)

---

