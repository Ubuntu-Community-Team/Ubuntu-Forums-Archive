---
title: "Weird problem about wired cards"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by mac75a on 2011-06-19
Hello guys,

I have a weird problem about my network cards:

I've been using my system normally for around 3 months, but some days ago I had to move the computer to another room, so I switched it off normally, unplugged all wires, moved the computer to another room, plugged all wires and when I switched it on I realized that my network card didn't work. All the lights on the card are switched off although it is connected by a LAN wire to the router. I think that maybe the card is disabled or blocked in some way, but I don't know how to unblock it (if this is the problem).

Well, when I bought the computer and installed Ubuntu 10.10 on it (around 3 months ago) I had a similar problem... It was impossible for me to get the onboard LAN card working (no lights on; it was activated in the BIOS), so I decided to install an old PCI Realtek card, which has been working until I moved the computer to another room :(

Now both cards are "disabled": No lights. And I don't know if it is a hardware problem (strange, at least one of the cards was working just before I switched the computer off, and stopped working when I switched the computer on 10 minutes later in another room) or if it is an Ubuntu problem (maybe it blocked the card?)

I have no other OS in the computer, maybe I will have to install a windows system to guess if the cards work on it, but before I hope to hear you guys, maybe someone gives me a clue about the problem. ;)

Here you have some information about the system:

###########################################

Ubuntu 10.10 Maverick Meerkat

###########################################

uname -a

Linux pcmigue 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

###########################################

ifconfig

eth0      Link encap:Ethernet  direcciónHW 20:cf:30:f3:81:d8  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:42 Dirección base: 0xa000 

eth1      Link encap:Ethernet  direcciónHW 00:c0:26:27:0f:ff  
          Direc. inet:192.168.0.2  Difus.:192.168.0.255  Másc:255.255.255.0
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:19 Dirección base: 0xe800 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:39 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:39 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3967 (3.9 KB)  TX bytes:3967 (3.9 KB)

vmnet1    Link encap:AMPR NET/ROM  direcciónHW   
          Direc. inet:172.16.170.1  Másc:255.255.255.0
          ACTIVO FUNCIONANDO  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet2    Link encap:AMPR NET/ROM  direcciónHW   
          Direc. inet:192.168.2.1  Másc:255.255.255.0
          ACTIVO FUNCIONANDO  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:AMPR NET/ROM  direcciónHW   
          Direc. inet:192.168.0.1  Másc:255.255.255.0
          ACTIVO FUNCIONANDO  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

###########################################

lshw -C network

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:f3:81:d8
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 10
       serial: 00:c0:26:27:0f:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.0.2 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e800(size=256) memory:febffc00-febffcff
  *-network:0
       description: interface
       physical id: 1
       logical name: /dev/vmnet1
       capabilities: physical
  *-network:1
       description: interface
       physical id: 2
       logical name: /dev/vmnet2
       capabilities: physical
  *-network:2
       description: interface
       physical id: 3
       logical name: /dev/vmnet8
       capabilities: physical

###########################################

lspci | grep Realtek

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

###########################################

lsmod | grep 81

8139too                19581  0 
8139cp                 16934  0 
r8169                  36521  0 
mii                     4425  3 8139too,8139cp,r8169

Thanks!!

---

### Post by mac75a on 2011-06-20
Nobody knows...?

---

### Post by nbound on 2011-06-20
Could be aq cabling problem, if you've got a laptop running ubuntu already and you know the ethernet works, plug it in, if no go, maybe the cabling is broken/shorted/semi/non-connected. Also try plugging the ethernet cable from that room into a different port on the router (its not all that uncommon for a single port to fail but the rest ok).

---

### Post by Iowan on 2011-06-20
Is the original location intact? That is, could you reconnect it where it worked - and see if it still does?

---

### Post by superduperlinuxperson on 2011-06-20
can we see :
rfkill list

---

