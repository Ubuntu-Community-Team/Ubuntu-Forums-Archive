---
title: "[SOLVED] Why can't I go faster than 1Mbps"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by joejoe148 on 2009-01-01
I cant seem to figure out to get my wireless to be all it can be.

I currently am connected at 1Mbps and every configuration attempt fails

In system>administration>network I am only able to connect in roaming mode.  If I try to manually configure it never works.

In "network tools" wlan0 shows up  and that is where I get the 1Mbps figure from but if I select Wlan0 and try to click configure i get and error message that the interface doesnt exist

Any help would be appreciated.  the specks from the sticky follow. I hope it isnt too long.



These are the specs:
Gateway laptop 200 ARC

02:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

wlan0     IEEE 802.11g  ESSID:"tweed"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:46:86:FA:3A   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=131/100  Signal level=-30 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

searching for modules brought up these that may be useful.  Tis is the only section with something that looked wireless

b43legacy             127776  0 
mac80211              165652  1 b43legacy
evdev                  13056  7 
cfg80211               15112  1 mac80211

ok, looking for messages with dmesg brought up a lot of stuff.  this is what looked right.

[  602.548513] b43legacy-phy0 debug: Using software based encryption for mac: ff:ff:ff:ff:ff:ff
[  602.549868] wlan0: Initial auth_alg=0
[  602.549874] wlan0: authenticate with AP 00:13:46:86:fa:3a
[  602.551381] wlan0: RX authentication from 00:13:46:86:fa:3a (alg=0 transaction=2 status=0)
[  602.551388] wlan0: authenticated
[  602.551392] wlan0: associate with AP 00:13:46:86:fa:3a
[  602.554841] wlan0: RX AssocResp from 00:13:46:86:fa:3a (capab=0x431 status=0 aid=2)
[  602.554846] wlan0: associated
[  602.554850] wlan0: CTS protection enabled (BSSID=00:13:46:86:fa:3a)
[  602.554854] wlan0: switched to short barker preamble (BSSID=00:13:46:86:fa:3a)
[  602.555140] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1413.256079] wlan0: no IPv6 routers present
[ 1423.568533] wlan0: no IPv6 routers present

OK here is the network configuration

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:00:00:60:32:f4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:2d:00:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.103 multicast=yes wireless=IEEE 802.11g

Ubuntu version is 8.04.1
kernal/architecture is 2.6.24-22-generic i686

---

