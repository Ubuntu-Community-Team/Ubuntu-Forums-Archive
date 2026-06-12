---
title: "Wireless Network Disconnected"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by thegutterpoet on 2013-01-27
My ubuntu 12.04 LTS never connected to my router wirelessly. I have to use a wired connection with an ethernet cable. The router is directly next to my PC. And the wireless connection works fine for everyone else in the house, two other Windows and an Apple Mac, and for my Windows package installed dually with Ubuntu.

How can I fix this?

---

### Post by Bucky Ball on 2013-01-27
Please provide the output of these two commands:

```
sudo lshw -C network
iwconfig
```

Thanks.

---

### Post by kulus1969 on 2013-01-27
semo@stephen:~$ sudo lshw -C network
[sudo] password for semo: 
Sorry, try again.
[sudo] password for semo: 
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:9e:d1:bc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.110 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 4c:0f:6e:2e:28:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:56000000-56003fff
semo@stephen:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

---

### Post by Bucky Ball on 2013-01-27
@ kulus1969: Please post a new thread regarding your issue rather than hijacking this one. It is unfair to the original poster, dilutes community effort, causes confusion, as is the case here, and is frowned upon. Persistent hijacking will attract warnings and/or suspensions.

@ thegutterpoet: Please post the output of these two commands:
```

sudo lshw -C network
iwconfig
```I notice on another thread you mention that the wireless has worked intermittently. Is that correct or not relevant to this card?

---

