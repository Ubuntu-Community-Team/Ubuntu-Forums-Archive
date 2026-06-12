---
title: "Broadcom Wireless don't broadcast in 11.04"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by MorganJarl on 2011-05-02
I have a Dell Vostro 1400 with a BCM4311 Broadcom wireless card that I just reinstalled with 11.04 from 10.04. I have the drives installed and it seams to be working when i run the 'Additional Drives', but I can't get the wireless adapter broadcasting. I followed the instructions given in the knowledge base on installing Broadcom Wireless, to see if I could get it running and that is where I saw the difference between the example and my computer when writing the 'sudo lshw -C network' command. In the example it said it was broadcasting under configuration (just like my wired networks below) and in mine it does not (see below for copy past). I can't find a tickbox in the systemtray to enable the wirless networking that I had before the update to 11.04 (the 'Enable Networking' tickbox is still there and the wired network works fine - that is how I got online to do this post). I have the hardware switch turned on and I have been in the BIOS and made sure that the Wireless is enabled.

Anyone who knows what could be wrong? Where could I go from here?

Thanks.

> morgan@morgan-Vostro-1400:~$ sudo lshw -C network
[sudo] password for morgan: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fd:a8:eb
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fe5f0000-fe5fffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 8e:24:ee:77:8f:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.100.100 link=yes multicast=yes

---

### Post by MorganJarl on 2011-05-03
I did the following and it helped me:

> **tacasi said:**
> Steve, I have the same wireless network card;  i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless  connection, even I cannot see the list of wireless networks) after the  11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source"  by using Synaptic Package Manager, then installing  "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package  Manager. I hope it solves your problem, too.

---

