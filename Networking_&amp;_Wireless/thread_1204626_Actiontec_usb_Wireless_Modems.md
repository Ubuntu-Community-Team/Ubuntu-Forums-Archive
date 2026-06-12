---
title: "Actiontec usb Wireless Modems"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by riccardo on 2009-07-05
Hello Aain...

I have Xubuntu 9.04 installed on this HP Omnibook Laptop (Model 510).  Wireless is giving me a pain ...   and I would appreciate any response from someone who can assist.

The response to lsusb is as follows:

Bus 003 Device 002: ID 1668:0408 Actiontec Electronics, Inc. [hex] Prism2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 15d9:0a37  
Bus 002 Device 003: ID 079b:004a Sagem XG-760A
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


... and you have to ignore the working usb wireless dongle ... which allows me to connect to the internet!!  Be advised that if I take it away ... nothing happens!

The response to the command 'iwconfig' is as follows:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0_rename  IEEE 802.11bg  ESSID:"south_flynn"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:19:DB:9C:F1:C0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:53/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     no wireless extensions.

pan0      no wireless extensions.


Where wlan0 in this case is the additional (and working) usb wifi dongle!

The response to ifconfig is as follows:

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:0a:92:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47600 (47.6 KB)  TX bytes:47600 (47.6 KB)

wlan0_rename Link encap:Ethernet  HWaddr 00:60:b3:e5:d3:c9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:b3ff:fee5:d3c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3683394 (3.6 MB)  TX bytes:565080 (565.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-60-B3-E5-D3-C9-33-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and my response to the command lshw -C network is as follows:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 42
       serial: 00:c0:9f:0a:92:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0_rename
       serial: 00:60:b3:e5:d3:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wlan1
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 52:b3:f0:2e:56:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

If any lister needs the output from other commands, please advise.  As I said above, I have a borrowed usb dongle that just works.  However, the in-built usb modem refuses to play ball.  I read that the last couple of releases of ubuntu have incorporated the prism2_usb cards into the standard kernel ... and that it should just work.  Can anyone please throw some ligh on this issue please??

riccardo

---

