---
title: "Toshiba U300 Wireless"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by hutchic on 2009-03-13
Hi all trying to get my wireless card working details bellow help is appreciated.  Sorry if I leave anything out don't follow the correct format etc:

Toshiba Satellite U300 Model Number PSU34C
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Ubuntu 8.10 2.6.27-11-generic i68

```

stacey@stacey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:63:fa:09  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe63:fa09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2398313 (2.3 MB)  TX bytes:401232 (401.2 KB)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5644 (5.6 KB)  TX bytes:5644 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:34:96:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-9E-34-96-45-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

stacey@stacey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

```

[  215.121188] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  215.232446] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

```

stacey@stacey-laptop:~$ iwlist scan
wlan0     No scan results

```

```

stacey@stacey-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:63:fa:09
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:34:96:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:33:83:13:4f:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

When I got System->Administration->Hardware Drivers Support fo 5xxx series Atheros 802.11 wireless LAN cards says a different version of this driver is in use.  Earlier this week enabling the driver got it working but that's not the case anymore.  At one point I tried installing the windows drivers when that didn't work I removed them...

Help appreciated.

---

