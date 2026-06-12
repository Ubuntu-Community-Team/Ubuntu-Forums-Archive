---
title: "Realtek 8185/Jaunty 9.04/Gateway W340UI Can't see wireless routers in NM"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Venlaar on 2009-09-15
I am trying to configure a Gateway laptop for a friend and am having trouble getting the wireless to work. Per [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI]("this link") the wireless card works out of the box in Dapper and Edgy. My friend is not that Linux savy so I would like to keep the configuration fairly simple in case he has to do it himself again later. Any help to get this working for him would be much appreciated.

Here is the configuration info: (I was connected via an ethernet cable while all the following were run) 

Machine Brand and Model: Gateway W340UI

Wireless Brand, Model and Wireless Chipset: 
```
$ lspci
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```

Check interface:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:3f:9b:9d  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe3f:9b9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635274 (635.2 KB)  TX bytes:116240 (116.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:cc:56:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-CC-56-B4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Check for modules:

```
$ lsmod | grep "rtl"
rtl8180                36864  0 
mac80211              217592  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               38288  2 rtl8180,mac80211

```

Kernel boot messages:
```
$ dmesg | grep "rtl"
[   12.454158] rtl8180 0000:08:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

[   12.658968] phy0: hwaddr 00:c0:a8:cc:56:b4, RTL8185vD + rtl8225

```

Network configuration:
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:3f:9b:9d
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=half firmware=N/A ip=192.168.1.103 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:cc:56:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:a1:0a:c7:dc:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Scan for networks:

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

Ubuntu Version:

```
$ lsb_release -d
Description:	Ubuntu 9.04

```

Kernel/architecture (including 32 vs. 64 bit): 

```
$ uname -mr
2.6.28-15-generic i686

```

Restarting the network:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

---

### Post by npallett on 2010-02-02
You need to download and compile the rtl-8185 linux driver from the [www.realtek.com](www.realtek.com) website.

I tried the 8180 but experienced the sames problems as yourself.

The 8185 driver works fine for me and I'm using with WPA2 Security on Ubuntu 8.04.4 32bit.

---

