---
title: "Intermittent Connectivity - Wired Router (WRT54g2)"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Waterboy5281 on 2010-11-10
To be brief, I am having intermittent connectivity issues with a wired connection to a WRT54G2 router.
I have no such issues if I am plugged straight into the modem.
My wireless persists throughout the outages and they usually require me to restart the interface on my machine.

I have used Wicd Network Manager and Ubuntu's out-of-the-box Network Manager.



Hopefully I'm not missing anything:

hostname -rs
```

Linux 2.6.32-25-generic

```
ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 00:04:5a:5f:54:b9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe5f:54b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:339358058 (339.3 MB)  TX bytes:26521564 (26.5 MB)
          Interrupt:22 Base address:0xb800 

```

lspci
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
02:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)
02:03.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

```

I have tried using Dynamic and Statis IPs:

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.102
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

OR

iface eth0 inet dhcp


```

lshw -C network
```

  *-network:0             
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:5f:54:b9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.102 latency=32 maxlatency=255 mingnt=255 multicast=yes
       resources: irq:22 ioport:b800(size=256) memory:feaffc00-feafffff memory:a0000000-a001ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 01
       serial: 00:07:e9:39:9a:f6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:feafe000-feafefff ioport:ac00(size=64)

```

No errors in dmesg.

Any ideas?

---

### Post by vladley on 2010-11-11
I'm having a VERY similar issue, I can't figure out if the problem is on my box or on my router.

Please help!

---

### Post by Whiteice on 2010-11-11
try removing the encryption on your router temp and see if the problem continues. If it does then it would possibly and issue with the router. If it stops then the encryption may be causing the problem you could try lowering it or changeing the algorithem.

---

