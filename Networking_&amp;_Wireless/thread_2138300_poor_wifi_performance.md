---
title: "poor wifi performance"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by icu12345 on 2013-04-23
Hi, I´m new to ubuntu and so I spent the past couple of days reading all sorts of stuff trying to get my WiFi working right. The problem is that internet is slow and I get very slow speed when copying files from my LAN. If connected by cable it´s all fine. The network itself is fine and the very same laptop had windows 7 previously and never had any Wifi trouble.

Here is the output of iwconfig (here is the moment to reveal that the wifi adapter supports just b/g, so 54 Mbps is perfectly fine):
```
icefire@Toshiba:~$ iwconfigwlan0     IEEE 802.11abg  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:B1:62:EE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:5600   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

And here is sudo lshw -C network

```
   *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:5d:46:ab
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:ae:d0:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-27-generic firmware=15.32.2.9 ip=192.168.1.20 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:d4200000-d4200fff



```


Do you think it could be a driver issue? I tried a lot of solutions I found in various forums but still have no luck.. Please help (bearing in mind that I´m new to linux so I´ll need detailed explanations...)

---

