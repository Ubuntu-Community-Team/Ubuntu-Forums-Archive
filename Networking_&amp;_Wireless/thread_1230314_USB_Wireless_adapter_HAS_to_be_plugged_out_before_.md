---
title: "USB Wireless adapter HAS to be plugged out before I boot up"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by bazm0 on 2009-08-03
[LEFT]Hello all, I relatively new to Ubuntu, and had to perform a couple of upgrades to get to 9.04 after installing an earlier version of Ubuntu on a partition. Anyways, here's the problem. I have installed the ndiswrapper packages and ndis gui package and successfully used the appropriate files for my WPN111 wireless USB adapter to get it up and running [although the nw icon hover text states "No network connection " & the wireless nw details are not persisted in the Network Connections Wireless tab !?!?] but now I find I need to plug my usb adapter out before I boot up in order for the adapter to be  recognised.
Here's the output from the following nw related commands:

barry@barry-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:61:a9:1c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:6d:93:5c:82:dc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:2f:b4:4b:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.53+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11g



barry@barry-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"UPC12"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:4A:36:14   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




barry@barry-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:61:a9:1c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b4:4b:8d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:feb4:4b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9716955 (9.7 MB)  TX bytes:1446738 (1.4 MB)


Come on chaps, what am I doing wrong? btw having issues using the Windows Wireless Drivers application (is this obsolete in 9.04?), getting erroneous error stating "Unable to see if hardare is present" - the gui does display whether it is present AND also getting genuine error stating "Could not find a netwotk configuration tool" when clicking on configure nw button. Maybe something went awry during the upgrades but any assistance would be great :confused:




[/LEFT]

---

