---
title: "Unable Getting SSI noise value in NEC WL300NC(ath9k)"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by sdcmtd on 2012-05-13
now. I want get SSI noise value in Radiotap header by wireshark(on ubuntu 10.04 LTS).
but I couldn't, so it became useless during the weekend.....
Then, there are some questions.

1.how to Get SSI noise value in NEC WL300NC(running with ubuntu 10.04 default ath9k)?
 
2.The conditions which acquire the value? (Device,DriverModule,Config..?)

I already succeeded getting other radiotap values(this card can set to monitor mode).
I trid update driver-module (compat-wireless2.6),but result doesn’t change. 

--------------------------------------------------------------------

lspci -nn | grep 'Atheros'
0b:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0023] (rev 01)

lsmod | grep "ath9k"
ath9k                  68107  0 
ath9k_common            2551  1 ath9k
ath9k_hw              223661  2 ath9k,ath9k_common
ath                     8041  2 ath9k,ath9k_hw
led_class               2864  1 ath9k
mac80211              225587  4 ath9k,ath9k_common,iwl3945,iwlcore
cfg80211              144778  6 ath9k,ath9k_common,ath,iwl3945,iwlcore,mac80211

sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:aa:bf:##
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.32-41-generic-pae firmware=15.32.2.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:cc000000-cc000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0a:08.0
       logical name: eth0
       version: 02
       serial: 00:1a:80:08:d9:##
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.4 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:d0005000-d0005fff ioport:6000(size=64)
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:0b:00.0
       logical name: wlan1
       version: 01
       serial: 00:0d:02:3b:54:##
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-41-generic-pae firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:48000000-4800ffff

lsb_release -d
Description:    Ubuntu 10.04.4 LTS

uname -mr
2.6.32-41-generic-pae i686

---

