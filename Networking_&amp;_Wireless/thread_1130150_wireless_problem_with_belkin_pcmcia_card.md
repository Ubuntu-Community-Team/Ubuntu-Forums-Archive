---
title: "wireless problem with belkin pcmcia card"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by coogy on 2009-04-19
hi 

i've installed xubuntu on an old ibm t20. all ok apart from connecting to my home wireless network. The card i'm using is a belkin 54g pcmcia card (ver 7000uk). 

I'm using ndiswrapper and the xp driver that came with the card.

ndiswrapper seems happy:-

[COLOR="Blue"]sean@sean-laptop:~$ !ndiswrapper
ndiswrapper -l
blkwgnv7 : driver installed
        device (1799:701F) present
[/COLOR]

but lshw reports two wired networks (the one descibed as CardBus is my wireless card) :-

[COLOR="Blue"]sean@sean-laptop:~$ sudo lshw -C network
  *-network               
       description: CardBus
       physical id: 0
       version: Fast Ethernet
       slot: Socket 0
       resources: irq:11
  *-network:0
       description: Ethernet interface
       product: RTL8139 [FE2000VX] CardBus Fast Ethernet Attached Port Adapter
       vendor: Abocom Systems Inc
       physical id: 2
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:98:a5:d1:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=ndiswrapper latency=0 maxlatency=64 mingnt=32
sean@sean-laptop:~$ 
[/COLOR]

[COLOR="Blue"]iwconfig doesn't see the card:-

sean@sean-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sean@sean-laptop:~$ 

[/COLOR]

anyone have any ideas where next?

---

### Post by coogy on 2009-04-19
*bump* (busy list)

---

