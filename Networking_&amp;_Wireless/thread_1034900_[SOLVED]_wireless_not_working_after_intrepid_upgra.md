---
title: "[SOLVED] wireless not working after intrepid upgrade"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by oskanaan on 2009-01-09
Hello,
Yesterday i upgraded my system to intrepid but my wireless connection is not working anymore, i browsed the forum for issues similar to this and i used ndiswrapper to install a windows driver but now i dont have wired connection also. when i run ifconfig i get that there is eth0 and wlan0, my interfaces file is as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.254.82
    netmask 255.255.255.0
    gateway 192.168.254.254

auto wlan0
iface wlan0 inet static
    address 192.168.254.82
    netmask 255.255.255.0
    gateway 192.168.254.254
    wireless-essid SpeedStream
    nameserver 195.229.241.222

my wireless card is intel 4965 AG or AGN, the laptop is a sony vaio fz460e

Please i'd appreciate any help i am stuck and i really need this to work

---

### Post by mikewhatever on 2009-01-09
When did you install ndiswrapper, before or after updating? Would you be so kind as to post the outputs of the following commands:
ifconfig
sudo lshw -C network

---

### Post by oskanaan on 2009-01-09
thanks for your reply

i used the wrapper after the upgrade

ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1a:80:a1:91:be  
          inet addr:192.168.254.82  Bcast:192.168.254.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3912 (3.9 KB)  TX bytes:3912 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:9b:80:63  
          inet addr:192.168.254.82  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe9b:8063/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26079 (26.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:fa000000-fa002000 


lshw -C network

 *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:9b:80:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.53+Intel,04/27/2007,11.1.0.100 ip=192.168.254.82 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:1a:80:a1:91:be
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.254.82 latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:5c:37:02:70:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by oskanaan on 2009-01-09
btw, when i click on the network connection icon in the tray i get the wired and wireless networks greyed out also i get "device is unmanaged" for both

---

### Post by oskanaan on 2009-01-09
After commenting everything except the following section
auto lo
iface lo inet loopback

in the interfaces file, everything is working fine now :D

---

