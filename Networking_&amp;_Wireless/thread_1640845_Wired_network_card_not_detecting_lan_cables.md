---
title: "Wired network card not detecting lan cables"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Stabback on 2010-12-08
Thanks for taking the time to help out.  I have a 64 bit install of Ubuntu 10.04, I was surfing up to 11:30pm EST last night, shut down for the night, upon reboot am unable to connect to the internet or my local network.  Ubuntu seems to think that I have no ethernet cables connected.

My networking is controlled by my motherboard (Gigabyte P55A-UD4P) and the problem is not on my cable modems side.  The modem has multiple wired jacks, all of them are unresponsive with my Ubuntu PC while my roommate can connect to all of them with his Windows 7 PC.  Both network cables (the one connecting to his box and the one connecting to mine) are interchangeable: They both work on his and neither on mine, so there is no broken cable.

I've followed the troubleshooting in other posts, here are some commonly requested diagnostics:
**ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:53:1f:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 6c:f0:49:53:1f:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:37 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1140 (1.1 KB)  TX bytes:1140 (1.1 KB)


```

**sudo lshw -C network**
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:53:1f:c0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:36 ioport:ae00(size=256) memory:fbbff000-fbbfffff(prefetchable) memory:fbbf8000-fbbfbfff(prefetchable) memory:fbb00000-fbb1ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 03
       serial: 6c:f0:49:53:1f:81
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:37 ioport:8e00(size=256) memory:fb9ff000-fb9fffff(prefetchable) memory:fb9f8000-fb9fbfff(prefetchable) memory:fb900000-fb91ffff(prefetchable)

```

Once again, thanks for taking the time to help.  The only way I can work is through this machine so it's fairly critical I get it up and running ASAP.

*Edit: It's worth noting that my mobo has two ethernet connections, however eth1 is actually covered by a metal door and is never in use.  I have tried using it in this case however it is as unresponsive as eth0.

---

### Post by Stabback on 2010-12-08
Follow up: Solved.  After trying every trick in the book I ended up hard booting (pulled the cord), went into my PC and removed my mobo's battery for a minute (removing the graphics card in the process, but obviously not a requirement for anyone else trying this).  After I plugged everything back in it's working fine (for now).  I hope this helps someone in the future!

---

