---
title: "Ethernet &quot;Cable Unplugged&quot; when it's not"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by Mr. Wishes on 2011-03-19
I'm using Kubuntu 10.10, and Network Management is saying that both of my ethernet cards are unplugged. While that is correct for eth0, eth1 should be working (it works in Windows, and used to work here until I installed a lot of updates recently).

I'm using wifi at the moment, which is working fine, but I'd prefer to use a wired connection.

I am reasonably proficient with linux, I've been using it for several years for work, and I'm perfectly happy to use the console and edit config files. I don't know the specifics of networking, though, so I don't know what information would help with diagnosis of the problem.

Here is ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:0f:c2:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 94:0c:6d:80:aa:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10208 (10.2 KB)  TX bytes:10208 (10.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:c7:79:47  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fec7:7947/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106772596 (106.7 MB)  TX bytes:8667174 (8.6 MB)


The output of lshw -C network:
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:0f:c2:c7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100MB/s
       resources: irq:50 ioport:9e00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff memory:fbd00000-fbd1ffff
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 10
       serial: 94:0c:6d:80:aa:c4
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:c800(size=256) memory:fb9ff000-fb9ff0ff memory:f0200000-f021ffff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan0
       serial: 00:17:3f:c7:79:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

I would have thought that this would work, but it doesn't.
> #ifconfig up eth1
eth1: Unknown host

Oddly, the output of ifquery --list is just 'lo'.

---

### Post by wyliecoyoteuk on 2011-03-19
It is showing both cards up, but without any IP address

try 
sudo ifconfig eth1 down
sudo ifconfig eth1 up

and see if that wakes it.

---

### Post by Mr. Wishes on 2011-03-19
Turns out it's not linux related, since I restarted into Windows and now it's not working there either. Oh well. Thanks for the advice anyway.

---

### Post by DrFolger on 2011-03-19
It's a known problem with the drivers related to your network card.
you need to completely shut off power (psu switch/unplug cord) to reset the network adapter when using the wrong driver ( r8169 )
 this link will show how to fix it by using the correct linux driver( r8168 ).

[http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B)

not sure why this problem has been around so long without being fixed....

---

