---
title: "Acer Aspire One AR8151 no internet"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by Hans Roels on 2010-10-28
Hello,

In installed Ubuntu 10.04 on an Acer Aspire One 721 but the wireless and wired network aren't working. I 've found some other threads about similar problems but this is quite confusing for me (quite new to Ubuntu). Can anyone tell me what I have to do? (I've read something in a thread about Madwifi...?)

This is the output of the command
sudo lshw -C network

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d0200000-d023ffff ioport:a000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0300000-d0303fff

It seems I have no drivers installed...

thanks,
Hansr

---

### Post by Darkaiser on 2010-10-31
try too look this thread
[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

---

