---
title: "WIRED internet connection NOT working"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by jagvir on 2009-12-29
[SIZE=2]i am using ubuntu9.10 in dual boot with window vista.i am using a cable internet provided by a Internet service provider (ISP) in india (vsnl). **There is no modem,just simple cable wire going into my LAN card**.
 My ISP has configured my net connection in vista with user name and password. As my ISP has no idea about how to confure it in ubuntu9.10, i had to do it myself. i had tried everything available on net to configure it but the end result was zero.o[/SIZE][SIZE=2][COLOR=Red]nce google opened after a long time 1 hr  1 am having 512 kbps connection.i think its working but very slow[/COLOR][/SIZE][SIZE=2]
 i am great fan of ubuntu but due to this silly reason i have to boot everytime in vista to surf. I am very much adamant to solve this problem.[/SIZE]



[SIZE=2]
[SIZE=4][COLOR=Red]i have attached screenshots of ubuntu configuration.for IPv6 i have tried all options from automatic to ignore ...nothing seems to work for me.

here is some information about my vista connection:[/COLOR][/SIZE][/SIZE][SIZE=4][COLOR=Red]
[/COLOR][/SIZE]
Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\king>ipconfig

Windows IP Configuration

[COLOR=Red]
Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : mshome.net
   IPv6 Address. . . . . . . . . . . : 2002:a294:129:a:3995:a7ac:a453:bdbe
   Site-local IPv6 Address . . . . . : fec0::a:3995:a7ac:a453:bdbe%1
   Temporary IPv6 Address. . . . . . : 2002:a294:129:a:71f4:b97b:1b96:3711
   Link-local IPv6 Address . . . . . : fe80::3995:a7ac:a453:bdbe%11
   IPv4 Address. . . . . . . . . . . : 162.148.1.55
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::bd71:921b:e877:f6be%11
                                       162.148.1.1[/COLOR]






[COLOR=Purple]
king@king-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:75:d6:52  
          inet addr:162.148.1.55  Bcast:162.148.1.255  Mask:255.255.255.0
          inet6 addr: fec0::a:221:70ff:fe75:d652/64 Scope:Site
          inet6 addr: 2002:a294:129:a:221:70ff:fe75:d652/64 Scope:Global
          inet6 addr: fe80::221:70ff:fe75:d652/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257434 (257.4 KB)  TX bytes:68920 (68.9 KB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:16:44:f4:c9:2b  
          inet6 addr: fe80::216:44ff:fef4:c92b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr de:a6:f9:37:46:f0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

king@king-laptop:~$ ifconfig -a
[/COLOR]









[COLOR=Lime]route table is

king@king-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.1         0.0.0.0         255.255.255.255 UH    0      0        0 eth0
162.148.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.1         0.0.0.0         UG    0      0        0 eth0
king@king-laptop:~$ [/COLOR]






[COLOR=Red]king@king-laptop:~$ udo dhclient eth0
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
udo: command not found
king@king-laptop:~$ sudo apt-get install dhcpd
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcpd has no installation candidate
king@king-laptop:~$ dhcpd eth0
No command 'dhcpd' found, did you mean:
 Command 'dhcpcd' from package 'dhcpcd' (universe)
 Command 'udhcpd' from package 'udhcpd' (universe)
 Command 'dhcpx' from package 'irpas' (multiverse)
dhcpd: command not found
king@king-laptop:~$ sudo lspci -C network
lspci: invalid option -- 'C'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
king@king-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:16:44:f4:c9:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:75:d6:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.09 ip=162.148.1.55 latency=0 multicast=yes
       resources: irq:30 memory:f69f0000-f69fffff
king@king-laptop:~$ 

[/COLOR]

---

### Post by jagvir on 2009-12-29
[SIZE=2]i am using ubuntu9.10 in dual boot with window vista.i am using a cable internet provided by a Internet service provider (ISP) in india (vsnl). **There is no modem,just simple cable wire going into my LAN card**.
 My ISP has configured my net connection in vista with user name and password. As my ISP has no idea about how to confure it in ubuntu9.10, i had to do it myself. i had tried everything available on net to configure it but the end result was zero.o[/SIZE][SIZE=2][COLOR=Red]nce google opened after a long time 1 hr  1 am having 512 kbps connection.i think its working but very slow[/COLOR][/SIZE][SIZE=2]
 i am great fan of ubuntu but due to this silly reason i have to boot everytime in vista to surf. I am very much adamant to solve this problem.[/SIZE]



[SIZE=2]
[SIZE=4][COLOR=Red]i have attached screenshots of ubuntu configuration.for IPv6 i have tried all options from automatic to ignore ...nothing seems to work for me.

here is some information about my vista connection:[/COLOR][/SIZE][/SIZE][SIZE=4][COLOR=Red]
[/COLOR][/SIZE]
Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\king>ipconfig

Windows IP Configuration

[COLOR=Red]
Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : mshome.net
   IPv6 Address. . . . . . . . . . . : 2002:a294:129:a:3995:a7ac:a453:bdbe
   Site-local IPv6 Address . . . . . : fec0::a:3995:a7ac:a453:bdbe%1
   Temporary IPv6 Address. . . . . . : 2002:a294:129:a:71f4:b97b:1b96:3711
   Link-local IPv6 Address . . . . . : fe80::3995:a7ac:a453:bdbe%11
   IPv4 Address. . . . . . . . . . . : 162.148.1.55
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::bd71:921b:e877:f6be%11
                                       162.148.1.1[/COLOR]






[COLOR=Purple]
king@king-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:75:d6:52  
          inet addr:162.148.1.55  Bcast:162.148.1.255  Mask:255.255.255.0
          inet6 addr: fec0::a:221:70ff:fe75:d652/64 Scope:Site
          inet6 addr: 2002:a294:129:a:221:70ff:fe75:d652/64 Scope:Global
          inet6 addr: fe80::221:70ff:fe75:d652/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:257434 (257.4 KB)  TX bytes:68920 (68.9 KB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:16:44:f4:c9:2b  
          inet6 addr: fe80::216:44ff:fef4:c92b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr de:a6:f9:37:46:f0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

king@king-laptop:~$ ifconfig -a
[/COLOR]









[COLOR=Lime]route table is

king@king-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.1         0.0.0.0         255.255.255.255 UH    0      0        0 eth0
162.148.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.1         0.0.0.0         UG    0      0        0 eth0
king@king-laptop:~$ [/COLOR]






[COLOR=Red]king@king-laptop:~$ udo dhclient eth0
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
udo: command not found
king@king-laptop:~$ sudo apt-get install dhcpd
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcpd has no installation candidate
king@king-laptop:~$ dhcpd eth0
No command 'dhcpd' found, did you mean:
 Command 'dhcpcd' from package 'dhcpcd' (universe)
 Command 'udhcpd' from package 'udhcpd' (universe)
 Command 'dhcpx' from package 'irpas' (multiverse)
dhcpd: command not found
king@king-laptop:~$ sudo lspci -C network
lspci: invalid option -- 'C'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
king@king-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:16:44:f4:c9:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:75:d6:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.09 ip=162.148.1.55 latency=0 multicast=yes
       resources: irq:30 memory:f69f0000-f69fffff
king@king-laptop:~$ 

[/COLOR]

---

### Post by Project PWNED on 2009-12-29
sudo dhclient eth0

---

### Post by Iowan on 2009-12-29
**ifconfig -a** produced a valid IP address - was that before or after installing **dhcpd** (this machine shouldn't need a DHCP server installed). the routing table (besides being hard to read) doesn't really look right (side effect of **dhcpd**?).
Another thing will be to check */etc/resolv.conf* for valid nameserver(s).

---

### Post by cariboo on 2009-12-29
Please don't create multiple threads on the same subject. I have merged your two threads.

---

