---
title: "Ubuntu is not connecting to the internet"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by BSOD64 on 2010-11-16
I plug my Ethernet cable into my laptop and I don't get any connection!:(
how can I fix this?:confused:

---

### Post by holiday on 2010-11-16
> **BSOD64 said:**
> I plug my Ethernet cable into my laptop and I don't get any connection!:(
how can I fix this?:confused:

Does your Ethernet cable connect to the machine you posted this message from?

---

### Post by BSOD64 on 2010-11-18
yes, that is the cable I am posting this from.

---

### Post by dineshs on 2010-11-18
Please post the results of the following terminal commands(applications- accessories-terminal```
sudo lshw -C network
```and ```
ping 209.85.231.104 -c3
```

---

### Post by BSOD64 on 2010-11-19
me@me-laptop:~$ sudo lshw -c network 
[sudo] password for me: 
  *-network               
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:f0100000-f0103fff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:24:e8:ea:05:0f 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s 
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 70:1a:04:a0:04:bc 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
me@me-laptop:~$ ping 209.85.231.104 -c3 
connect: Network is unreachable

---

### Post by dineshs on 2010-11-20
> *-network DISABLED 
If you are using Network manager ensure that enable networking is ticked
(Rightclick NM icon ie the icon on top right of the panel)
OR use the following code
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```and see that ```
NetworkingEnabled=true
WirelessEnabled=true
```
Hope it is enabled in BIOS

---

### Post by jpl888 on 2010-11-20
You could try manually setting an ip address and default route. From a terminal:-

```
sudo -s
ifconfig eth0 192.168.x.x
route add default gw 192.168.x.x
```

Where x.x is in the first instance is a free address on your network and in the second the ip address of you router.

Post the results of "ifconfig" and "route" after you have done that to confirm things are ok and try an external ping again.

---

### Post by BSOD64 on 2010-11-20
thank you dineshs!:D

your fix worked!:D

(you forgot to tell me I had to reboot);)

---

### Post by dineshs on 2010-11-21
> **BSOD64 said:**
> 
(you forgot to tell me I had to reboot);)
:)
Happy to hear that your problem is solved

---

