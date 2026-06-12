---
title: "wireless not functioning / Toshiba Satellite pro U 400 / 10.04 LTS"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by moblid on 2010-05-06
Hi, 
I installed ubuntu today and the after a while the wireless stopped working (at first it did). I'm very inexperienced in these things so don't even really know how to search for answers... though I tried the troubleshooting in this forum and didn't get through it. 
Anyway here is the information I managed to find meanwhile: 


07:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16) 
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100 


Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 002: ID 15d9:0a4c Dexon 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 004: ID 04f2:b064 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:34:3b:16  
          inet6 addr: fe80::221:6bff:fe34:3b16/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:27339 (27.3 KB)  TX bytes:22360 (22.3 KB) 

wlan0     IEEE 802.11abgn  ESSID:"BEN-ISHAY"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1B:9E:D8:4D:42   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

  *-network               
       description: Ethernet interface 
       product: Marvell Technology Group Ltd. 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       logical name: eth0 
       version: 16 
       serial: 00:23:8b:30:54:0e 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:27 memory:80400000-80403fff ioport:3000(size=256) memory:80600000-8061ffff(prefetchable) 
  *-network 
       description: Wireless interface 
       product: Wireless WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:21:6b:34:3b:16 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:29 memory:80800000-80801fff 

I'm not sure how much of this is relevant... 
Many thanks for any help!
Moshe

---

