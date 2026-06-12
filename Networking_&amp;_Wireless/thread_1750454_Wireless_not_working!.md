---
title: "Wireless not working!"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by KaiJordanDay on 2011-05-05
Laptop: Fujitsu Siemens Li 1718
Wireless Card: AR5001

It worked on 10.10 but does not on 11.04. Can't Access internet to install updates either!

Outputs:

iwconfig

lo
eth0

ifconfig
etho
lo

lspci shows my Atheros AR5001 wireless card

---

### Post by josephmills on 2011-05-05
ok could we please see a 
```
dmesg | grep ath
```
and a 
```

lsmod | grep ath

```
this last one takes a while to load but here it is 
```

sudo lshw -C network

```
please paste all the results here thanks you

---

### Post by KaiJordanDay on 2011-05-05
> kai@Kai-LAPTOP:~$ dmesg | grep ath
[    1.211649] device-mapper: multipath: version 1.2.0 loaded
[    1.211657] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.631158] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   21.631168] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   21.631194] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   21.634403] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
kai@Kai-LAPTOP:~$ lsmod | grep ath
kai@Kai-LAPTOP:~$ sudo lshw -C network
[sudo] password for kai: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:64:1b:25
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:a000(size=256) memory:c0200000-c02000ff
kai@Kai-LAPTOP:~$ 



Took a while, USB's decided to stop working too!

---

### Post by josephmills on 2011-05-05
> **KaiJordanDay said:**
> Took a while, USB's decided to stop working too!

you do not need the ndiwrapper please uninstall it what version of ubuntu are you using? you need the ath5k mod/driver and firmware this should come out of the box. but you have to first uninstall ndiswrapper then go to ubuntu software center then go to edit-->software sources please make sure that all are ticked see pic then then close software sources thenn open your terminal again and type in 
```
sudo apt-get update 
```
then 
```

sudo apt-get upgrade 

```
then 
```

sudo reboot 

```
after rebooting let us know how it works out:)

---

### Post by KaiJordanDay on 2011-05-05
I can't get on the internet, so I can't update...

Im using 11.04.

It worked on 10.10 out-of-the-box before upgrading to 11.04

---

### Post by josephmills on 2011-05-05
bummer I am sure that some one know who to get the ath5k installed with-out the net but that some one is not me sorry but good luck

---

### Post by samsankey on 2011-05-06
Surely you can plug your laptop into your router with an ethernet cable and upgrade?

---

### Post by KaiJordanDay on 2011-05-07
Ok so bridged PC and Laptop, ran updates and no wireless on restart still.

---

