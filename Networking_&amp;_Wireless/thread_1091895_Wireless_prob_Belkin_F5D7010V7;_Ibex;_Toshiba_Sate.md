---
title: "Wireless prob: Belkin F5D7010V7; Ibex; Toshiba Satellite A40-S270 laptop"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by yugffuts on 2009-03-09
Trying to connect my ubuntu (Ibex) laptop to my linksys wireless G router (WRT54GX4).  I can see the network, as well as others (neighbors?).  I can attempt to connect, but it stalls on the DHCP stage.  I have reset the router to factory settings, but still no luck.  I have posted all the outputs below in case there are any clues.  I'm a relative newbie to ubuntu, so any tips would be helpful.  I'm thinking Ubuntu is correct, and the router is the problem, but I figured i'd ask before I bought a new router.

lspci
02:00.0 Ethernet controller: Belkin Device 701f (rev 20)

lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Net_123456"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:10:C7:93:91   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=33/100  Signal level:19/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:8e:7b:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 20
       serial: 00:17:3f:30:9e:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:bf:20:d7:ed:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:C7:93:91
                    ESSID:"Net_123456"
                    Mode:Master
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=60/100  Signal level:23/65  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000004835f182
                    Extra: Last beacon: 596ms ago

uname -mr
2.6.27-11-generic i686

---

### Post by yugffuts on 2009-03-14
Bought a new router, now it is working.  Does anyone answer questions in this forum?  This is the second or third time I was on my own after asking for guidance....

---

