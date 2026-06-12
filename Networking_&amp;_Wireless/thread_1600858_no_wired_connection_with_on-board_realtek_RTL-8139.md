---
title: "no wired connection with on-board realtek RTL-8139"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by Fezzz on 2010-10-19
Hi, I have just installed xubuntu 10.10 on an old computer assembled with some different parts of others. 
 I made the installation with alternate cd and it was all ok except a  message that said something like "cannot configure internet connection".  I ignored it thinking it was possible to configure the connection later  but now I can't connect to the internet. I don't think it's an hardware  problem neither something due to the bios because till few days ago I  had ubuntu 9.10 on the same computer and the connection worked fine.
I tried to take a look around the forum searchin a solution but I haven't found it.
Can you help me?

Below there are the outputs of some commands that I hope will be useful also if I haven't precisely idea of what is their significance.

```

sudo lshw -C network                     
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth1
       version: 10
       serial: 00:0f:ea:f0:23:06
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:c000(size=256) memory:de004000-de0040ff


ifconfig                                           
eth1      Link encap:Ethernet  HWaddr 00:0f:ea:f0:23:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8064 (8.0 KB)  TX bytes:8064 (8.0 KB)

lspci -nn | grep Ethernet                          
00:13.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


dmesg | grep 00:13                                 
[    0.101807] pci 0000:00:13.0: reg 10: [io  0xc000-0xc0ff]
[    0.101814] pci 0000:00:13.0: reg 14: [mem 0xde004000-0xde0040ff]
[    0.101847] pci 0000:00:13.0: supports D1 D2
[    0.101849] pci 0000:00:13.0: PME# supported from D1 D2 D3hot
[    0.101854] pci 0000:00:13.0: PME# disabled
[    1.345367] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.988433] 8139too 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.989295] 8139too 0000:00:13.0: eth0: RealTek RTL8139 at 0xc000, 00:0f:ea:f0:23:06, IRQ 18


lsmod | grep 8139   
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp

```

---

### Post by darab on 2010-10-19
Try this first:

sudo ifdown eth1 
sudo dhclient eth1

---

### Post by Fezzz on 2010-10-19
```

sudo ifdown eth1         
ifdown: interface eth1 not configured
   

sudo dhclient eth1 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:0f:ea:f0:23:06
Sending on   LPF/eth1/00:0f:ea:f0:23:06
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Another thing. In the icon in the notification area the network is enabled but, if I click on it to select a connection, the list is empty and the only thing that I can see in the section Wired Network is "disconnected" even if I insert the ethernet cable.
And only to be sure...when I run the commands of which I posted the outputs I was always working with the ethernet cable inserted.

---

### Post by eshaputra on 2011-11-09
> **Fezzz said:**
> ```

sudo ifdown eth1         
ifdown: interface eth1 not configured
   

sudo dhclient eth1 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:0f:ea:f0:23:06
Sending on   LPF/eth1/00:0f:ea:f0:23:06
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Another thing. In the icon in the notification area the network is enabled but, if I click on it to select a connection, the list is empty and the only thing that I can see in the section Wired Network is "disconnected" even if I insert the ethernet cable.
And only to be sure...when I run the commands of which I posted the outputs I was always working with the ethernet cable inserted.

Bump!...
I have the same problem above...
any solution maybe?
I have been searching around and find nothing really help me...

---

