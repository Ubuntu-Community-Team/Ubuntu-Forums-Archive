---
title: "No Wired Connection on eMachine E525 with Ubuntu 8.04"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Refresher on 2009-06-16
I installed Ubuntu 8.04 on my eMachine E525 but it seems that Wired Connection is not supported because I can't find option of wired connection in Network Settings? Is this something to do with my machine? Any ideas how to establish wired connection?

---

### Post by Refresher on 2009-06-16
lspci output:
Ethernet controller: Attansic Technology Corp. Unknown device 1062 (rev c0)

Please help me to get drive for ethernet that Ubuntu would recognise!

---

### Post by superprash2003 on 2009-06-16
post output of
1)lshw -C network
2)ifconfig

---

### Post by Refresher on 2009-06-16
signe@signe-laptop:~$ lshw -C network
 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:24:2c:4f:17:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
signe@signe-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:2c:4f:17:81  
          inet6 addr: fe80::224:2cff:fe4f:1781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:5
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73600 (71.8 KB)  TX bytes:73600 (71.8 KB)

THANKS

---

### Post by mess110 on 2009-08-20
same problem here

Ok I managed to get wireless connection.

To get wireless connection I went to System > Administration > Hardware drivers and I enabled alternate Atheros "madwifi" driver. Now I did a ```
sudo apt-get update
``` and I am installing updates.

Going to keep you posted

ok after updating No network devices avaliable :(

next step: I disabled the madwifi drivers and it works now. but only wireless

ok more ppl to help us please? still trying. gonna download drivers and compile them. maybe it will work

---

