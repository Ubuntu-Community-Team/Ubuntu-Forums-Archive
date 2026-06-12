---
title: "Atheros AR5005G Wireless not working"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by david.e.brock on 2009-02-13
I have been trying to get my wireless card to work now for around 15 hours. it is an Atheros AR5005G Wireless card. After spending hours searching through the internet I could still get nothing to work. Here is my configuration:

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:1e:68:55:87:78
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe55:8778/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3763257 (3.7 MB)  TX bytes:743217 (743.2 KB)
          Interrupt:20 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7200 (7.2 KB)  TX bytes:7200 (7.2 KB)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


lshw (this is the part with the network info)
> *-network:0                                                                                                                                       
                description: Ethernet interface                                                                                                              
                product: RTL-8139/8139C/8139C+                                                                                                               
                vendor: Realtek Semiconductor Co., Ltd.                                                                                                      
                physical id: 2                                                                                                                               
                bus info: pci@0000:08:02.0                                                                                                                   
                logical name: eth0                                                                                                                           
                version: 10                                                                                                                                  
                serial: 00:1e:68:55:87:78                                                                                                                    
                size: 100MB/s                                                                                                                                
                capacity: 100MB/s                                                                                                                            
                width: 32 bits                                                                                                                               
                clock: 33MHz                                                                                                                                 
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                                    
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.8 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s                                                                                            
           *-network:1 UNCLAIMED                                                                                                                             
                description: Ethernet controller                                                                                                             
                product: AR2413 802.11bg NIC                                                                                                                 
                vendor: Atheros Communications Inc.                                                                                                          
                physical id: 4                                                                                                                               
                bus info: pci@0000:08:04.0                                                                                                                   
                version: 01                                                                                                                                  
                width: 32 bits                                                                                                                               
                clock: 33MHz                                                                                                                                 
                capabilities: pm bus_master cap_list                                                                                                         
                configuration: latency=80 maxlatency=28 mingnt=10

I have tried madwifi and it does not work. I am using kernel version 2.6.28.2

---

### Post by ugm6hr on 2009-02-14
Try the [ath5k driver]("apt:linux-backports-modules-intrepid-generic") - which works for the AR2413 / AR5007 chipset.

You will have to disable the Atheros HAL / ndiswrapper / madwifi drivers, if you have tried any of them.

---

### Post by david.e.brock on 2009-02-14
how would I do that?

---

### Post by ugm6hr on 2009-02-14
Get online with wired.

Use the link above.

Undo anything you have tried before - what have you tried?

---

