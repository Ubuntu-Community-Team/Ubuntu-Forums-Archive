---
title: "internet connection stopped working after update"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by mice80 on 2012-02-29
Hello,

I`m having problems with my broadband connection. The computer can connect to my router and other computers in my network and all the other computers can access this computer. But I have no internet connection. 

If I change 
**managed=false  - > true**
in  /etc/NetworkManager/nm-system-settings.conf


I can get internet to work but I cannot asign a static IP and the computer is not visible in my home network so no other computer can access it.

any kind of help appreciated !!!


xxxxxxxxxxxxxx:~$ cat /etc/issue

Ubuntu 10.04.4 LTS \n \l

xxxxxxxxxxxx:~$ lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

mice@mice-xbmc:~$ uname -a

Linux mice-xbmc 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux


xxxxxxxxxx:~$ ifconfig

> 
eth0      Link encap:Ethernet  HWaddr 00:13:72:d3:f4:85
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fed3:f485/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:404223 (404.2 KB)  TX bytes:8936945 (8.9 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:146521 (146.5 KB)  TX bytes:146521 (146.5 KB)
xxxxxxxxxxx:~$ cat /etc/NetworkManager/nm-system-settings.conf

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        network 192.168.1.2
        broadcast 192.168.1.255
        gateway 192.168.1.1
# This file is installed into /etc/NetworkManager, and is loaded by
# NetworkManager by default.  To override, specify: '--config file'
# during NM startup.  This can be done by appending to DAEMON_OPTS in
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1d:60:ce:f6:1f,

[ifupdown]
managed=false
xxxxxxxxxxxx:~$ cat /etc/network/interfaces

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        network 192.168.1.2
        broadcast 192.168.1.255
        gateway 192.168.1.1
xxxxxxxxxxxx:~$ sudo lshw -C network

> 
*-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:d3:f4:85
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.44a ip=192.168.1.120 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:fe8f0000-fe8fffff


Mice

---

