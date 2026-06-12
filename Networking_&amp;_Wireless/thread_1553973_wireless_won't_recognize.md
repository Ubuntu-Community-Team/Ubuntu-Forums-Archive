---
title: "wireless won't recognize"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by ex_isp on 2010-08-15
Greetings.  Thanks in advance for any help!

Have done:
root@chris-laptop:/home/chris# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:d0:59:3a:0b:74  
          inet addr:192.168.211.107  Bcast:192.168.211.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe3a:b74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395560 (395.5 KB)  TX bytes:72359 (72.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
and

root@chris-laptop:/home/chris# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:3a:0b:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.211.107 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:41280000-41280fff ioport:3440(size=64) memory:41200000-4121ffff memory:24100000-241fffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:18000000-18007fff

and

got driver 

ran  apt-get update
then make
then make install.

Still get
root@chris-laptop:/home/chris# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:3a:0b:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.211.107 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:41280000-41280fff ioport:3440(size=64) memory:41200000-4121ffff memory:24100000-241fffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:18000000-18007fff


Am using Ubuntu 10.04 with all updates.
Wireless card is CNET CWC-854

HELP!!!  

Ex

---

### Post by ex_isp on 2010-08-16
bump

---

### Post by shoppertrip on 2010-08-16
jesus..really dazzled by this...we need a real professional here

---

### Post by ex_isp on 2010-08-17
bump

---

### Post by ex_isp on 2010-08-17
bump again?  No one?  Need some guru help here please...?

---

### Post by ercferret18 on 2010-08-17
what messages did you get when you typed in "make install"?

---

### Post by ex_isp on 2010-08-17
dont remember exactly, but was not indicative of error...said ~ok and returned prompt

will run again and post exact

---

### Post by ex_isp on 2010-08-17
root@chris-laptop:/home/chris/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module# make installmake -C /lib/modules/2.6.32-24-generic/build \
    INSTALL_MOD_DIR=extra SUBDIRS=/home/chris/Desktop/2010_0412_RT61_Linux_STA_v1.1.2.5/Module \
    modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  DEPMOD  2.6.32-24-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
Network device directory /etc/sysconfig/network-scripts
Module configuration file /etc/modprobe.conf 
/sbin/depmod -a

then returned prompt

card powers up and works fine on this old laptop with win, but dont even get power light in Lin.

---

### Post by ex_isp on 2010-08-18
'nother bump

guru help please?  ideas?

---

