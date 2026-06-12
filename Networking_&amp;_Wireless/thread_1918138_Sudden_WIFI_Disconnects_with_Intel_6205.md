---
title: "Sudden WIFI Disconnects with Intel 6205"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by slowcodetochina on 2012-01-31
hey guys, relatively new to linux.

im running a 64bit ubuntu **11.10**/7 dualboot, and when I can wrangle a wifi connection with my intel 6205, it lasts for like a minute, then switches off and tries to reconnect.
posting this on the ethernet connection, which is fine

I tried this: [http://ubuntuforums.org/showthread.php?t=1739047&page=4](http://ubuntuforums.org/showthread.php?t=1739047&page=4)
didn't work

It was worse with network-manager, but at least with wicd the disconnects are more predictable.

i'd appreciate any and all help, 

lspci -nn

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: A4:0C:C3:96:7B:C0   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -c network

 *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a0:88:b4:91:5e:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.0.0-12-generic firmware=17.168.5.3 build 42301 ip=172.26.195.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:ddc00000-ddc01fff

---

### Post by ashlanky on 2012-03-06
Having this exact same problem. Tried following the fix in this thread to no avail. 
[http://ubuntuforums.org/showthread.php?t=1908026](http://ubuntuforums.org/showthread.php?t=1908026)

---

