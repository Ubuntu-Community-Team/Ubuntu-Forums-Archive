---
title: "WiFi disabled on Compaq nx6325 laptop"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by rtrinkner on 2010-04-13
Hello,

This is my first post on Ubuntu forums, after successfully installing Ubuntu 9.10 on my Compaq nx6325 laptop.

The laptop connects to the wired Internet OK through the Ethernet port.

The WiFi, however, shows no networks in the vicinity, when I know that there are many networks that should be available.  In Windows, the same laptop locates my home network and logs on just fine.

I've tried some troubleshooting.

Here is what the lshw command reported:

richard@richard-laptop:~$ sudo lshw -C network
[sudo] password for richard: 
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c8000000-c8003fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:17:08:2e:d4:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5788-v3.26 ip=192.168.1.104 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:23 memory:d4000000-d400ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:e1:aa:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


I then tried to install the Windows Wireless Driver package, with apparent success.  I was able to run the program and specify the .inf file that I downladed from HP (now owners of the Compaq brand).   When I specify the .inf file in the WWD package, it reports "Unable to see if hardware is present." 

I'm a Linux noob.  

Thanks very much!

---

### Post by dgw on 2010-04-13
go to System > Administration > Hardware Drivers

What do you see there? Do you have the option to install the Broadcom STA wireless driver? If you do, try that.

---

### Post by rtrinkner on 2010-04-13
When I go to System -> Administration -> Hardware Drivers, I receive a blank text box that reports "No proprietary drivers are in use on this system" at the top.  There is no option to add drivers.

---

### Post by rtrinkner on 2010-04-13
Solved: after updating the system files, the problem was solved. The error seems to have been a bug in the 9.10 distribution, but is solved after updating on 13 April 2010.

---

