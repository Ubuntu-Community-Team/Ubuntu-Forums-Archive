---
title: "Lenovo Ideapad wireless just deactivated; not the switch"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by dundeej5 on 2010-02-01
I really cannot explain this, as this morning my wireless worked marvelously.  However, upon a restart, WICD ceased seeing anything at all (except wired connections).  I have completed Ubuntu's tutorials, run update, & run ifconfig, iwconfig, & lshw -C network (printed below), but know too little about this language and its options available to me to solve the problem (which I don't really understand).  It seems to me that the wireless card is on, but ceased functioning--why, I haven't a clue.

Thanks for helping

jonathan@Hypericum:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:cd:fb:07  
          inet addr:128.223.147.253  Bcast:128.223.147.255  Mask:255.255.254.0
          inet6 addr: 2001:468:d01:92:223:5aff:fecd:fb07/64 Scope:Global
          inet6 addr: fe80::223:5aff:fecd:fb07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3966552 (3.9 MB)  TX bytes:565864 (565.8 KB)
          Interrupt:29 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:f7:67:26  
          inet6 addr: fe80::221:ff:fef7:6726/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jonathan@Hypericum:~$ sudo lshw -C network
[sudo] password for jonathan: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:f7:67:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:56100000-56103fff
  *-network
       description: Ethernet interface
       ...
physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=128.223.147.253 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256) memory:52010000-52010fff(prefetchable) memory:52000000-5200ffff(prefetchable) memory:52020000-5203ffff(prefetchable)
jonathan@Hypericum:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions. ](*,)

---

