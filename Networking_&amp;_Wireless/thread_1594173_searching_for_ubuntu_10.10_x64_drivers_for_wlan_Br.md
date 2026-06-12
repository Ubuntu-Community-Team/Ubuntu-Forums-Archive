---
title: "searching for ubuntu 10.10 x64 drivers for wlan Broadcom BCM4322 on vostro 1520"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Michael REMY on 2010-10-12
hi,

my OS is linux ubuntu x64 v10.10 on netbook dell vostro 1520.
i'm looking for wlan [[COLOR=#00c800][COLOR=#00C800 ! important][FONT=arial][COLOR=#00C800 ! important][FONT=arial]drivers[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://phoronix.com/forums/showthread.php?p=152044#") for network adapter broadcom like this:

     Quote:
                                                 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)                                 
shall you help me please ?

---

### Post by Peter09 on 2010-10-12
You need to use a hardwired link to upgrade your system (if this is a new install) then check in
 
System->Admin->Hardware
 
for any drivers you need to enable - Broadcom drivers should work more-or-less out of the box.

---

### Post by Michael REMY on 2010-10-12
thank for your reply.

it is an upgrade from the previous release, not a new clean install.

before (in previous release), the drivers worked rightly.

that's why i don't understand the problem since the upgrade.

any clue to help me ?

---

### Post by Peter09 on 2010-10-12
Have you checked
 
System->Administration->Hardware
 
if so can you post the output of
 
```
ifconfig
```
 
and
 
```
lshw -C network
```

---

### Post by Michael REMY on 2010-10-12
ifconfig :

> 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:b4:3b:25  
          inet adr:192.168.1.132  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::224:e8ff:feb4:3b25/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:37076 erreurs:0 :0 overruns:0 frame:0
          TX packets:34008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:10808457 (10.8 MB) Octets transmis:6938663 (6.9 MB)
          Interruption:47 

eth1      Link encap:Ethernet  HWaddr 00:24:2c:39:eb:5d  
          adr inet6: fe80::224:2cff:fe39:eb5d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:18 

eth1:avahi Link encap:Ethernet  HWaddr 00:24:2c:39:eb:5d  
          inet adr:169.254.6.165  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:18 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:10392 erreurs:0 :0 overruns:0 frame:0
          TX packets:10392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:6461489 (6.4 MB) Octets transmis:6461489 (6.4 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet adr:192.168.56.1  Bcast:192.168.56.255  Masque:255.255.255.0
          adr inet6: fe80::800:27ff:fe00:0/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:7395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:1841327 (1.8 MB)




> 
-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:b4:3b:25
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.132 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2c:39:eb:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fa000000-fa003fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.56.1 multicast=yes


---

### Post by Peter09 on 2010-10-12
Can you do the two commands without the hardwire link. Other than that it looks good.

---

### Post by CarbineReloaded on 2010-10-16
Having the same problem

eth0      Link encap:Ethernet  HWaddr 00:1e:68:12:a5:48  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe12:a548/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2178 errors:38 dropped:0 overruns:0 frame:38
          TX packets:2469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1094880 (1.0 MB)  TX bytes:664781 (664.7 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:f2:71:ce  
          inet6 addr: fe80::21a:73ff:fef2:71ce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:314175 (314.1 KB)  TX bytes:314175 (314.1 KB)


 *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:12:a5:48
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.107 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:f2:71:ce
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by Peter09 on 2010-10-16
Can you d this without the hardwired link connected.

---

### Post by CarbineReloaded on 2010-10-16
> **Peter09 said:**
> Can you d this without the hardwired link connected.

eth0      Link encap:Ethernet  HWaddr 00:1e:68:12:a5:48  
          inet6 addr: fe80::21e:68ff:fe12:a548/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7322 errors:149 dropped:0 overruns:0 frame:149
          TX packets:7362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6331634 (6.3 MB)  TX bytes:1507268 (1.5 MB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:f2:71:ce  
          inet6 addr: fe80::21a:73ff:fef2:71ce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:487980 (487.9 KB)  TX bytes:487980 (487.9 KB)


 *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:12:a5:48
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.107 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:f2:71:ce
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by CarbineReloaded on 2010-10-16
Oddly enough even though my Wifi doesn't work.... when I connect my Motorola Droid running 2.2 to my laptop, I'm able to teather via usb without issues......  atleast that still works in addition to the hardwired connection that's across the house.

---

### Post by halj32 on 2010-10-16
to get your wifi working by installing dkms, fakeroot, patch and then the bcmwl-kernel-source package

if your not online they are on the cd/pool

---

### Post by Peter09 on 2010-10-16
You still have another conection - so I cannot tel what is happening. You need to do ifconfig when the wireless should be trying to connect.

---

### Post by CarbineReloaded on 2010-10-16
What other connection do I have? THe droid being teathered was not connected to the laptop, the wired connection was disconnected.

I have no options to select Wifi at all on the laptop... everything worked on 10.4 but died on 10.10.

When I click to select a wireless network from the icon up top.... it says "no network devices available"

---

