---
title: "No Internet, LAN or Wireless"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by vincentertainment on 2010-03-24
I have a fresh install of Karmic on a older compaq laptop.
I initially had LAN access, but not wifi. I added a few Broadcom packages using synaptic, and then neither worked. Then I removed the same packages, but I still have no internet access, LAN or wifi.

Here are some of my settings.
```

```      vincentertainment@vincentertainment-laptop:~$ iwconfig
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  wmaster0  no wireless extensions.
  
   
   
  wlan0     IEEE 802.11bg  ESSID:""  
  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
  
            Tx-Power=0 dBm   
  
            Retry  long limit:7   RTS thr:off   Fragment thr:off
  
            Power Management:off
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
   
   
  vincentertainment@vincentertainment-laptop:~$ sudo lshw -C network
  
  [sudo] password for vincentertainment: 
  
    *-network:0             
  
         description: Ethernet interface
  
         product: RTL-8139/8139C/8139C+
  
         vendor: Realtek Semiconductor Co., Ltd.
  
         physical id: 0
  
         bus info: pci@0000:05:00.0
  
         logical name: eth0
  
         version: 10
  
         serial: 00:16:36:29:4a:8f
  
         size: 100MB/s
  
         capacity: 100MB/s
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.105 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
  
         resources: irq:18 ioport:a000(size=256) memory:d0208000-d02080ff
  
    *-network:1
  
         description: Network controller
  
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
  
         vendor: Broadcom Corporation
  
         physical id: 2
  
         bus info: pci@0000:05:02.0
  
         version: 02
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master
  
         configuration: driver=b43-pci-bridge latency=64
  
         resources: irq:20 memory:d0204000-d0205fff
  
    *-network DISABLED
  
         description: Wireless interface
  
         physical id: 1
  
         logical name: wlan0
  
         serial: 00:14:a5:71:57:58
  
         capabilities: ethernet physical wireless
  
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  
  vincentertainment@vincentertainment-laptop:~$ ifconfig -a
  
  eth0      Link encap:Ethernet  HWaddr 00:16:36:29:4a:8f  
  
            inet addr:192.168.15.105  Bcast:192.168.15.255  Mask:255.255.255.0
  
            inet6 addr: fe80::216:36ff:fe29:4a8f/64 Scope:Link
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:13628 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:1214093 (1.2 MB)  TX bytes:23070 (23.0 KB)
  
            Interrupt:18 Base address:0xa000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
  
   
   
  wlan0     Link encap:Ethernet  HWaddr 00:14:a5:71:57:58  
  
            BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
   
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-71-57-58-00-00-00-00-00-00-00-00-00-00  
  
            [NO FLAGS]  MTU:0  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)```

```

---

### Post by Iowan on 2010-03-24
If the results are current, eth0 seems to have an IP address. If you know your router's address, you could try to **ping** it (by name or address). If successful, you may have DNS (*/etc/resolv.conf*) or routing (**route -n**) problem.

---

