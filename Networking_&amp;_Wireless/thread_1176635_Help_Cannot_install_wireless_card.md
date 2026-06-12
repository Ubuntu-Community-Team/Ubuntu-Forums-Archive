---
title: "Help Cannot install wireless card"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by cephus6 on 2009-06-02
Trying to install WCE600n wireless card.

Here is more info, if someone could tell me what is going on or point me in the right direction. I am still new to Linux and I have followed so many guides I am not sure what I have installed.

I can see my wireless network in the network manager, but it will not connect.


lspci -v | less

01:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
Subsystem: Linksys Device 0068
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at c4000000 (64-bit, non-prefetchable) [size=16K]
Memory at c9000000 (64-bit, prefetchable) [size=1M]
Capabilities: <access denied>
Kernel driver in use: ndiswrapper
Kernel modules: ssb, wl

lshw -c network

*-network
description: Wireless interface
product: BCM4328 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
logical name: wlan1
version: 03
serial: 00:21:29:d0:84:e7
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. ip=192.168.2.150 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: 3e:e0:49:e3:31:1a
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

wlan1 IEEE 802.11g ESSID:"Home"
Mode:Managed Frequency:2.437 GHz Access Point: 00:90:4C:EC:00:2A
Bit Rate=130 Mb/s Tx-Power:32 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:78/100 Signal level:-46 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

ifconfig

eth0 Link encap:Ethernet HWaddr 00:1e:68:03:25:66
inet addr:192.168.2.133 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::21e:68ff:fe03:2566/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5114 errors:0 dropped:0 overruns:0 frame:0
TX packets:4936 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4828572 (4.8 MB) TX bytes:821392 (821.3 KB)
Interrupt:20 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:49 errors:0 dropped:0 overruns:0 frame:0
TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4572 (4.5 KB) TX bytes:4572 (4.5 KB)

wlan1 Link encap:Ethernet HWaddr 00:21:29:d0:84:e7
inet addr:192.168.2.150 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::221:29ff:fed0:84e7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:95 errors:0 dropped:0 overruns:0 frame:0
TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:10724 (10.7 KB) TX bytes:3997 (3.9 KB)
Interrupt:17 Memory:c4000000-c4004000


Any assitance would be appreciated

---

### Post by peterthewolf on 2009-06-02
Search forums for BCM4328 there is plenty of advice.

---

### Post by shanix on 2009-06-02
[https://bugs.launchpad.net/bugs/365857](https://bugs.launchpad.net/bugs/365857)

In /etc/rc.local file, add the following two lines and reboot:

rmmod ssb
modprobe wl

---

### Post by cephus6 on 2009-06-02
Shanix

Thank you.  That appears to fixed the problem.

I have been pulling out my hair with this problem.

I really appreciate your time.

---

