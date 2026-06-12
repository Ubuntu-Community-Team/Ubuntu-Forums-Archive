---
title: "Wireless connection always fails the first time"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by colecovision on 2009-06-25
I have wubi (Jaunty) installed on an MSI Wind.

At first, wireless (Dlink router) worked fine. Then for some reason, it stopped working. I've tried a bunch of different things, I'm now at the point where it consistently times out the first time I try to connect, then at least succeeds the second time.

I am using Wicd (after uninstalling Network Manager). When it fails the first time, it gets to the point of making DHCPREQUESTs and then eventually quits with a no DHCPOFFERS received message. The second time it usually quickly succeeds.

Any idea how I can get this thing to connect without having to wait for it to time out so I can try again?

---

### Post by Crafty Kisses on 2009-06-25
Just for starters, what are the results of these commands?
```
lshw -C network
ifconfig
iwconfig
```

---

### Post by colecovision on 2009-06-25
lsconfig -C network

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:63:34:7d
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:24:21:45:7d:2a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=0 module=rtl8187se multicast=yes wireless=802.11b/g linked
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:43:7f:60:e3:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:21:63:34:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:38584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37273477 (37.2 MB)  TX bytes:7195966 (7.1 MB)
          Interrupt:253 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6551 (6.5 KB)  TX bytes:6551 (6.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:21:45:7d:2a  
          inet6 addr: fe80::224:21ff:fe45:7d2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27219 errors:352 dropped:23384 overruns:0 frame:0
          TX packets:23244 errors:11 dropped:90 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30930587 (30.9 MB)  TX bytes:3990306 (3.9 MB)
          Interrupt:18 Memory:f7df8000-f7df8100 


iwconfig

wlan0     802.11b/g linked  ESSID:"nobody you know"  
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:24:01:44:D7:8E   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/100  Signal level=-42 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Aat on 2009-08-05
I have the same problem on my eeepc 901. It fails to connect on the first try, a second time it does work. I'm hoping someone has an answer...

---

