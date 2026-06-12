---
title: "Eee 1005HA wireless working in one spot but not another."
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by Odzinic on 2012-09-13
Hi there,
I recently installed Ubuntu on my Eee for university. The first day that I used it at the university I had no problems until I suspended it and came back later to see the wireless has been disconnected and it is not finding any signals. I used my phone to see if wifi was in range and it indeed was.

Here is some information:

lspci -nn | grep 'Atheros':

> Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)


iwconfig and ifconfig:

> lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:75:83:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43193 (43.1 KB)  TX bytes:43193 (43.1 KB)

usb0      Link encap:Ethernet  HWaddr f6:dc:4f:c4:4b:76  
          inet addr:192.168.42.253  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::f4dc:4fff:fec4:4b76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1561077 (1.5 MB)  TX bytes:574160 (574.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:ca:67:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwlist scan:

> lo        Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.


sudo lshw -C network

>  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:ca:67:1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:75:83:6d
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: f6:dc:4f:c4:4b:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.253 link=yes multicast=yes


I have to go to a lecture now, so if there is any other information needed please ask and I will post it.

Thanks

---

