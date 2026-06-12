---
title: "trying to diagnose wireless problem but rfkill commands not working; please help"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by bringingdadaback on 2011-07-14
Hello,

Yesterday after a computer crash (ubuntu 11.04) my wireless (ralink 5390) suddenly stopped working. In trying to fix the problem, I searched the forums and it seems that my wireless may be blocked. 

However, none of the rfkill commands work. Rfkill list and rfkill unblock do absolutely nothing. I've even installed and uninstalled rfkill twice.

Is there a way to change this manually? Or perhaps a way to return ALL network related configurations to default?

Some info:

lshw -C network

> *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:93500000-9350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 2c:27:d7:d5:49:04
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig
> eth0      Link encap:Ethernet  HWaddr 2c:27:d7:d5:49:04  
          inet6 addr: fe80::2e27:d7ff:fed5:4904/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3724258 (3.7 MB)  TX bytes:769202 (769.2 KB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by chili555 on 2011-07-14
> *-network [COLOR="Red"]UNCLAIMED[/COLOR]
description: Network controller
product: Ralink corp.
vendor: Ralink corp.
physical id: 0Your wireless card doesn't have a driver attached. Did you compile it? Does it come to life if you do:```
sudo modprobe rt5390sta
```Are there any errors following that command?

---

### Post by bringingdadaback on 2011-07-14
Hi Chili,

Thanks for your reply. Your posts about applying the ralink patches were the ones that originally helped me get my wireless up and running a few weeks ago.

sudo modprobe rt5390sta gives me:

> FATAL: Module rt5390sta not found.

Well, that certainly doesn't look good.

---

### Post by chili555 on 2011-07-14
Well, then I suggest you rebuild the module. The patches are already done, so you may safely skip that part.```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su
make clean
make
make install
modprobe rt5390sta
exit
```Of course, substitute your details if the RT5390 folder is not in Documents. Post back if it all doesn't go perfectly!

---

### Post by Bucky Ball on 2011-07-14
Posted in error. ;)

---

### Post by bringingdadaback on 2011-07-14
It worked! Thank you chili!

Marking as solved; maybe this can help someone else.

---

