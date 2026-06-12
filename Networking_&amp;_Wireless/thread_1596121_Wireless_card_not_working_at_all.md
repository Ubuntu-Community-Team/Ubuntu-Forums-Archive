---
title: "Wireless card not working at all"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Vaultx on 2010-10-13
I am dual booting Windows 7 and Ubuntu 10.10 64-bit. I did a fresh install of 10.10 instead of updating 10.04, and my wireless hasn't worked since then. In 10.04 it worked fine with no effort. Now my card won't even recognize any nearby connections. 

Computer model: Asus CM5570

lspci
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: RaLink RT2860

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:26:18:bd:60:b8  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:febd:60b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116211603 (116.2 MB)  TX bytes:4233912 (4.2 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21274 (21.2 KB)  TX bytes:21274 (21.2 KB)


```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```
sudo lshw -C network
```
  *-network DISABLED      
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:65:58:70
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:26:18:bd:60:b8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:e800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```

I hope I've posted enough information. Any help is very appreciated! (Hopefully fairly quick because I have limited access to a wired connection and booting to Windows and back is not fun. :(  )

---

### Post by Vaultx on 2010-10-14
anyone?

---

