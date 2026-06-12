---
title: "need help with hp 110"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by lunchbox910 on 2010-06-16
I am really new to Ubuntu and put Netbook Remix on my computer (110-1025). For some reason I cannot connect to wired or wireless at all.  I have read lots of threads about HP mini connectivity problems and tried to follow the steps.  Most cases people were only having wireless problems and could still do things wired.  

I totally need some help here...  I am not on my own computer now so I'll have to check back later.  I know I didn't provide much info so I'm sure there will be some questions I will have to answer.

Thanks so much or any help.

Chris

lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:24:81:6d:9e:61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:26 memory:febc0000-febfffff ioport:ec80(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2c:87:e4:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg





lspci -vnn | grep l4e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)



sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:6d:9e:61  
          inet6 addr: fe80::224:81ff:fe6d:9e61/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:54534873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:47278 (47.2 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10720 (10.7 KB)  TX bytes:10720 (10.7 KB)

sudo dhclient eth0
Listening on LPF/eth0/00:24:81:6d:9e:61
Sending on   LPF/eth0/00:24:81:6d:9e:61
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Russell Burrows on 2010-10-05
bump

---

