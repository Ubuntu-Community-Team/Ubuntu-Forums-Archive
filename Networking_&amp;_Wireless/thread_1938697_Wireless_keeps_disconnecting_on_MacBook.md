---
title: "Wireless keeps disconnecting on MacBook"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by Hetepeperfan on 2012-03-10
Dear community,

I like to use my  MacbookPro with Ubuntu. So I added ubuntu to my laptop which runs fabulous. I always have a excellent signal strength. However, for reasons I don't understand the Gnome Network utility keeps connecting and disconnect all the time and I need to fillout the network key again, or actually just press enter/ok-button since the key is correct. Now my Questions are the following why does the network disconnect and connect all the time? And the second, how can I fix this?

so i run the following code:

```
maarten@maarten-laptop:~$ lspci -v | grep -i network
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
maarten@maarten-laptop:~$ lspci -v | grep -i network > network
networking/  network.txt  
maarten@maarten-laptop:~$ lspci -v | grep -i network > network.txt 
maarten@maarten-laptop:~$ ifconfig >> network.txt 
maarten@maarten-laptop:~$ iwconfig >> network.txt 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

maarten@maarten-laptop:~$ lsmod | grep -i "wlan_module_name" >> network.txt maarten@maarten-laptop:~$ dmesg | grep -i "wlan_module_name" >> network.txt 
maarten@maarten-laptop:~$ sudo lshw -C network >> network.txt 
[sudo] password for maarten: 
maarten@maarten-laptop:~$ lsb_release -d >> network.txt 
maarten@maarten-laptop:~$ uname -mr  >> network.txt 
maarten@maarten-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
maarten@maarten-laptop:~$ 

```the the contents of network.txt is:

```
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
eth0      Link encap:Ethernet  HWaddr c8:bc:c8:90:a2:61  
          inet6 addr: fe80::cabc:c8ff:fe90:a261/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11802166 (11.8 MB)  TX bytes:2111638 (2.1 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 78:ca:39:bb:13:81  
          inet6 addr: fe80::7aca:39ff:febb:1381/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:96220 errors:2 dropped:0 overruns:0 frame:189369
          TX packets:61421 errors:279 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124239319 (124.2 MB)  TX bytes:7538350 (7.5 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:595515 (595.5 KB)  TX bytes:595515 (595.5 KB)

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:170
          Rx invalid nwid:0  invalid crypt:36  invalid misc:0

  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 78:ca:39:bb:13:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:22 memory:d3200000-d3203fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: c8:bc:c8:90:a2:61
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5764m-v3.38 latency=0 link=no multicast=yes port=twisted pair speed=1GB/s
       resources: irq:27 memory:d3100000-d310ffff
Description:    Ubuntu 10.04.4 LTS
2.6.32-38-generic x86_64

```Any help would be much appreciated!

Maarten

---

