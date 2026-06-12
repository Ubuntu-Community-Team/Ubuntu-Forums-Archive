---
title: "wireless problems"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Biceptoid on 2009-07-12
ok im on a g50v asus laptop. my graphics card is an atheros. im duel booting windows and ubuntu. when im on ubuntu my computer cant connect to wireless. all the options are greyed out so i cant even chose to use wireless. ive added my wireless connection anyways and it establishes connection but i recieve no internet. im not sure what to do . please help

---

### Post by superprash2003 on 2009-07-13
post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

---

### Post by The Toxic Mite on 2009-07-13
I will make it clearer for you:

[indent]
Go to Applications > Accessories > Terminal, and type in the following commands:
```

lshw -c network
iwconfig

```

Post the outputs when you are done. :)
[/indent]

---

### Post by Biceptoid on 2009-07-13
heres the code output
 
kevin@kevin-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
PCI (sysfs) 
*-network 
description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 01
serial: 00:15:af:ce:be:1e
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k ip=10.42.43.1 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 02
serial: 00:22:15:3a:37:cb
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 42:b6:e9:48:f0:fc
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kevin@kevin-laptop:~$ 
kevin@kevin-laptop:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:"pathos" 
Mode:Ad-Hoc Frequency:2.412 GHz Cell: C6:4B:75:36:8A:B7 
Tx-Power=20 dBm 
Retry min limit:7 RTS thr:off Fragment thr=2352 B 
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.
kevin@kevin-laptop:~$

---

### Post by superprash2003 on 2009-07-14
you seem to be connected with a 10.42.43.1 ip to pathos  . post output of
1)ifconfig
2)route -n

---

### Post by Biceptoid on 2009-07-14
kevin@kevin-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:22:15:3a:37:cb 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:247 Base address:0xc000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:1440 (1.4 KB) TX bytes:1440 (1.4 KB)
wlan0 Link encap:Ethernet HWaddr 00:15:af:ce:be:1e 
inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0
inet6 addr: fe80::215:afff:fece:be1e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:3669 (3.6 KB)
wmaster0 Link encap:UNSPEC HWaddr 00-15-AF-CE-BE-1E-65-31-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
kevin@kevin-laptop:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.42.43.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
kevin@kevin-laptop:~$ 
 
  thats the output to ifconfig and route -n

---

### Post by superprash2003 on 2009-07-15
ok , you seem to be connected to an ad-hoc network , is that correct?

---

### Post by Biceptoid on 2009-07-19
yep. i can connect to the internet though a wired connection. just not a wireless.

---

