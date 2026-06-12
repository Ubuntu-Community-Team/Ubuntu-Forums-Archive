---
title: "error network UNCLAIMED"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by james a on 2010-12-01
Hi, 
 
I am not able to configure ubuntu 9.04 on network ,
 
i get error 
 
Network UNCLAIMED    .... error 
 
[INDENT]ethernet controller is BROADCOM Corporation Device 1692 ( rev 01)
 
 
 
Pls help
[/INDENT]

---

### Post by Iowan on 2010-12-01
Wow... 9.04 is what I run on my laptop... What are results (from a terminal) of **sudo lshw -C network** 
I suspect a driver problem - drivers are one of my weak areas... :(

---

### Post by gordintoronto on 2010-12-01
I suggest Ubuntu 10.10. It has much better Broadcom support.

---

### Post by james a on 2010-12-02
Hi, 
 
Pls find below the result of lshw -C network & lspci.
 
 
As suggested i have installed 10.10 & the same is working fine 
 
can you suggest any solution for 9.04, since some of my clients are using 9.04 & the same has to be configured in this 
 
 
[EMAIL="root@ubuntu:/home/tts4"]root@ubuntu:/home/tts4[/EMAIL]# lshw -C network
  
*-network UNCLAIMED     
       
description: Ethernet controller
       
product: Broadcom Corporation
       
vendor: Broadcom Corporation
       
physical id: 0
       
bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       
version: 01
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress bus_master cap_list
       
configuration: latency=0
  *-network DISABLED
       
description: Ethernet interface
       
physical id: 1
       
logical name: pan0
       
serial: 9a:c7:37:ef:5a:19
       
capabilities: ethernet physical
       
configuration: broadcast=yes driver=bridge driverversion=2.3 
firmware=N/A link=yes multicast=yes
 

[EMAIL="root@ubuntu:/home/tts4"]root@ubuntu:/home/tts4[/EMAIL]# lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation Device 1692 (rev 01)

---

