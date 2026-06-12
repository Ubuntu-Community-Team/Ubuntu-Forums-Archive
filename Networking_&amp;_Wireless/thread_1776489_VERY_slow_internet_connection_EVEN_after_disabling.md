---
title: "VERY slow internet connection EVEN after disabling IPv6 Ubuntu 11.04"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by volto on 2011-06-06
Hello,

I installed ubuntu yesterday on my desktop. I noticed that the global internet connection is very slow (browsing,downloading from apt-get, etc). I followed the guides to disable ipv6 but it didn't help. I don't know what's wrong, maybe it's my drivers? Please help!!!

---

### Post by ubgeek on 2011-06-06
I'm having similar problem....but my net speed is ok while browsing but very slow on downloading...i disabled ipv6 but no luck....i tried to update  my wireless driver but couldnot do it as i'm also a noob....

is there any way to update wlan driver thru terminal command line...

my wlan device is 

Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

thanks..

---

### Post by ratcheer on 2011-06-06
Disabling IPv6 is not a cure all. IPv6 is rarely the cause of peoples' connectivity problems.

I recommend [http://www.dslreports.com](http://www.dslreports.com) where they specialize in diagnosing and correcting these kinds of troubles.

Tim

---

### Post by maxfire2020 on 2011-09-17
make this file 

gedit /etc/pm/power.d/wireless


add this code
> 

#!/bin/sh
/sbin/iwconfig wlan0 power off




and may goad be whit you

bye

---

### Post by varunendra on 2011-09-18
volto and ubgeek,

I can't assure of a solution, but would like to try. Please open a terminal and enter these commands (after using the connection for a couple of minutes):
```
sudo lshw -C network
```
and
```
ifconfig -a
```

The first one will give us network related hardware and associated driver details, the second one will verify if it is a 'packet-dropping' case.

If it is a wireless interface, then also-
```
iwconfig
```
 It is same as ifconfig, but provides more details about wireless interfaces.

---

### Post by gnusci on 2011-09-18
Add the System Monitor applet to one of the panels, use the preferences to monitor your Network.

---

### Post by praty888 on 2011-11-15
[COLOR=Red]sudo lshw -C network[/COLOR]

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:a2:70:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f6cf0000-f6cfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:22:19:f7:e0:c5
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:ce00(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff memory:f0220000-f023ffff

[COLOR=Red]iwconfig[/COLOR]

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SP_101"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:BB:50:E0   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:190   Missed beacon:0

---

