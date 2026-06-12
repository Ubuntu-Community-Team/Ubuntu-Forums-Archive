---
title: "Network stoped working after update (newbie user)"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by brunoja on 2009-11-09
Hello!

I had Ubuntu 9.04 and I set up manually an ad-hoc network to use my friend internet (I dont want to buy routers or anything ). Here is the file interfaces:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
wireless-mode ad-hoc
wireless-channel 4
wireless-essid Shareme
wireless-key 1234567890
address 100.0.0.2
netmask 255.255.0.0
gateway 100.0.0.1
nameserver 100.0.0.1

```It was working before the update, and now after it, its not working anymore, and I cant ping my friends computer (100.0.0.1). I tried a sudo /etc/init.d/networking restart and got this error:

```
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
SIOCDELRT: No such process
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.

```What is wrong :confused:

Thank you!

---

### Post by Iowan on 2009-11-09
Post results of **lshw -C network** and **ifconfig -a**

---

### Post by brunoja on 2009-11-09
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:5b:32:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:58:e0:1a
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:6000(size=256) memory:f8410000-f8410fff(prefetchable) memory:f8400000-f840ffff(prefetchable) memory:f8420000-f842ffff(prefetchable
```

and

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:58:e0:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:5b:32:49  
          inet6 addr: fe80::223:4eff:fe5b:3249/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:3077
          TX packets:30 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3444 (3.4 KB)  TX bytes:4497 (4.4 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

The bcmwl-kernel-source is installed! :/ What is wrong?

---

### Post by Iowan on 2009-11-09
I suspect you already tried rebooting the machine? Sometimes it seems more thorough than a restart - since that doesn't necessarily make NM "resync".

---

### Post by brunoja on 2009-11-10
I restarted many times but no results :/

---

### Post by brunoja on 2009-11-10
Well, this is completely weird! I tried to connect via nm-applet and now its working o.O (it was disabled, I re-enabled it)
Before the update the nm-applet only gave me headaches, so I did it manually, now it saved my life :lolflag:

---

