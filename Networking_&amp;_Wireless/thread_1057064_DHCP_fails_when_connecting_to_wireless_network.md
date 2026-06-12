---
title: "DHCP fails when connecting to wireless network"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by Windrabbit on 2009-02-01
I'm running Intrepid on an MSI Wind U100. I can connect to a wired network. I've installed the driver for the wifi card. I use wicd, and it displays a list of all wireless networks correctly. However, when I try to connect to my WPA-encrypted one or any unsecured network, I can't get an IP. What should I do?

---

### Post by Windrabbit on 2009-02-01
```

emannes@borg-1:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:e5:d9:f6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:21:85:86:88:e9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=0 module=r8180 multicast=yes wireless=802.11b/g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:03:36:04:2b:b0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

emannes@borg-1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

emannes@borg-1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:e5:d9:f6  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fee5:d9f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30140 errors:0 dropped:3068680387 overruns:0 frame:0
          TX packets:28825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29227626 (29.2 MB)  TX bytes:5110164 (5.1 MB)
          Interrupt:221 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25310 (25.3 KB)  TX bytes:25310 (25.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:85:86:88:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:17038 overruns:0 frame:0
          TX packets:17943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:740124 (740.1 KB)
          Interrupt:17 Memory:f8b20000-f8b20100 

emannes@borg-1:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

---

