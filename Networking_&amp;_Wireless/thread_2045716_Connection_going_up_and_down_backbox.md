---
title: "Connection going up and down backbox"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by satoshy on 2012-08-21
Hello, i'm doing my first Linux esperiments using BackBox from usb key but i've a strange problem.

The connection is slow and sometimes it goes off for some minutes.. Then it go up.. ADSL is ok and works well in Windows 7 installation 

I hope anyone can help me

---

### Post by satoshy on 2012-08-22
Up! help

Here some comands informations

[B]ipconfig
[/B][HTML]
eth0      Link encap:Ethernet  HWaddr c8:60:00:e3:26:87  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fee3:2687/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1024 errors:0 dropped:1024 overruns:0 frame:1024
          TX packets:1090 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086611 (1.0 MB)  TX bytes:149002 (149.0 KB)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2243 (2.2 KB)  TX bytes:2243 (2.2 KB)
[/HTML]

[B]iwconfig
[/B][HTML]
lo        no wireless extensions.

eth0      no wireless extensions.
[/HTML]

**sudo lshw -C network**
[HTML]
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:e3:26:87
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
[/HTML]


**nm-tool**
[HTML]
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        C8:60:00:E3:26:87

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
[/HTML]

2 min ago the connection show Connected but i can't navigate on internet :-//

---

