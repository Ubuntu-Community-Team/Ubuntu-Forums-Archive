---
title: "Dell Inspiron 530S - Wifi Won't Connect"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by qazwart on 2009-05-01
I have a Dell Inspiron 530S and am having problems getting the WiFi to work. I see the WiFi icon in the panel, and I see the various WiFi networks, but it doesn't connect to any of them.

Here is the output from the various hardware and network commands. I've also attached a few of the files from the /var/log directory that seemed to be involved in this:

lspci
=====
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

ifconfig -a
===========

eth0 Link encap:Ethernet HWaddr 00:21:9b:24:25:cc
inet addr:192.168.0.107 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::221:9bff:fe24:25cc/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:15764 errors:0 dropped:0 overruns:0 frame:0
TX packets:8689 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:22679938 (22.6 MB) TX bytes:693994 (693.9 KB)
Memory:fdfc0000-fdfe0000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

pan0 Link encap:Ethernet HWaddr 92:b4:d3:ca:37:29
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr 00:24:8c:04:73:02
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-24-8C-04-73-02-00-00-00-00-00-00-00-00-00-00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

iwconfig
===

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

pan0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=20 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

lshw -C network
===============
*-network
description: Ethernet interface
product: 82562V-2 10/100 Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 02
serial: 00:21:9b:24:25:cc
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=192.168.0.107 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:24:8c:04:73:02
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 92:b4:d3:ca:37:29
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by RedSingularity on 2009-05-03
Follow [this](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/) guide.  It is VERY helpful with your wireless card.

---

### Post by qazwart on 2009-05-03
> **Shadow121 said:**
> Follow [this](http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/) guide.  It is VERY helpful with your wireless card.

I had already followed Sambar's guide. When we first installed Ubuntu, the drivers didn't load because we weren't connected to the Internet because the WiFi wasn't working. So, we moved the system across our house, connected it via Ethernet to the router, then tried System->Administration->Hardware Drivers. It didn't find the needed drivers. 

We then followed the above Sambar's directions, manually installed the drivers, and rebooted. We could now see the various WiFi networks, but couldn't connect to any of them. That's when I emailed the forum.

My son decided our best bet is to reinstall Ubuntu 9.04, but this time while connected to the Internet via the Ethernet cable. This time, System->Adminstration->Hardware Drivers detected the B43 Broadcom drivers. We were able to do the download and install. We then rebooted, and everything worked.

Issue Resolved

---

