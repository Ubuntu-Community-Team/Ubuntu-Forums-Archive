---
title: "Internet stopped working after hard reboot"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by Joseph_Dantes on 2011-12-05
My girlfriend power cycled the computer accidentally, and now the internet has stopped working.

I can still access the network. Just not the internet. For example, my Synergy still works. 

When I try to visit any website, Chrome tells me that DNS lookup failed. Firefox doesn't work either. Nor can I connect to my VPN.

I will now describe my setup:

Ubuntu 11.04 - the Natty Narwhal 
Desktop computer
Ethernet cable connection to Chinese ISP provided router. 
Router also connects to two Windows laptops via ethernet cable. Both can access the internet. 

ifconfig output:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:18:a4:1b:8d  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea4:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1081443 (1.0 MB)  TX bytes:795796 (795.7 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:503978 (503.9 KB)  TX bytes:503978 (503.9 KB)

ip route output:

$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.101  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 
dunpeel@dunpeel-desktop:~$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.101  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

The modem is set to DHCP

Can anyone help? I have no clue what to do. I read the forums and tried various restart/reset commands, and disabled my firewall. None of this helped. 

I'm guessing there's some kind of config file problem that got borked on the hard reboot, but I don't even know how that's possible. There were a couple of hard reboots the day before, and they didn't produce this reaction. 

Should I go for a recovery disk or what?

EDIT: Some additional networking output:


$ sudo lshw -C network
[sudo] password for dunpeel: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:30:18:a4:1b:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:ee00(size=256) memory:fdbff000-fdbfffff memory:fdbe0000-fdbeffff memory:fdb00000-fdb1ffff

---

