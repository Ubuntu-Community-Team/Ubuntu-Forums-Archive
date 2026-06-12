---
title: "wireless works but I can connect"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by tazz34 on 2010-11-16
Hello everyone,

I have soamsung rs-620-js01tr notebook. It has ar5001atheros wireless network card. It sems like working but I cannot connect to my wireless modem (windows 7 , xp connects without problems) .I have multiboot: windows 7 , Ubuntu 10.10 and 8.10 (backtrack4 r1) . Both ubuntu versions has connectivity problem. My modem has wpa2 security and password is true. 

Here some results:
~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:4d:6f:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f6000000-f600ffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:24:54:16:09:d7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.2.43 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:fa000000-fa003fff ioport:5000(size=256) memory:f4000000-f401ffff


Thank u for your assistance.

---

### Post by dineshs on 2010-11-16
what happens(post the result of sudo lshw -C network) if you remove your ethernet cable and try?

---

### Post by tazz34 on 2010-11-16
Thank u for your interest. Not connected
here is the result:
,
lshw -C network
: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:4d:6f:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f6000000-f600ffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:24:54:16:09:d7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:fa000000-fa003fff ioport:5000(size=256) memory:f4000000-f401ffff

---

### Post by dineshs on 2010-11-16
What about ```
iwconfig
```and```
sudo dhclient wlan0
```

---

### Post by tazz34 on 2010-11-16
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
:/etc$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:26:b6:4d:6f:c0
Sending on   LPF/wlan0/00:26:b6:4d:6f:c0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by dineshs on 2010-11-18
Did you connect wireless before trying the commands?(You should)

---

