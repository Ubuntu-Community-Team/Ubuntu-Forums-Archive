---
title: "Wlan connects but does not work after upgrade to 12.04.1"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by martinilinski on 2012-10-31
Hallo,
after upgrading ubuntu the network  manager still connects to wlan, but internet doesn't work and I can't ping/ reach the wlan router's homepage.

lshw -C network and iwconfig give the following output:

martin@martef:~$ sudo lshw -C network
[sudo] password for martin: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:86:52:2c:8c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:ad:7d:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-31-generic firmware=228.61.2.24 ip=192.168.1.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:df2fe000-df2fffff
martin@martef:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"mainstation"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:49:E0:1B:DE   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0

eth0      no wireless extensions.

Thanks for helping!

---

