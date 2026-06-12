---
title: "need help with new realtek usb wireless in 10.04"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by mejbr2003 on 2012-03-16
Hi, 
I just installed a realtek usb wireless adapter. I installed it in xp and it worked fine.
I dual boot lucid. in lucid the network manager seems to see my network "netgear"...but won't allow me to connect.
I did the ndisgtk thing and installed the windows driver 
any ideas 
thanks for any help...

here are the the outputs I'm guessing you might ask for

j@mydamncomputer:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan2 802.11b/g/n ... ESSID:"Kiyoshi"
Mode:Managed Frequency=2.437 GHz Access Point: 00:21:29:67:4C:5A
Bit Rate=130 Mb/s
Retry min limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
j@mydamncomputer:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan2 802.11b/g/n ... ESSID:"NETGEAR"
Mode:Managed Frequency=2.447 GHz Access Point: 00:22:3F:B5:89:26
Bit Rate=130 Mb/s
Retry min limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
j@mydamncomputer:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:15:f2:a8:78:c2
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:588 errors:0 dropped:0 overruns:0 frame:0
TX packets:588 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:46640 (46.6 KB) TX bytes:46640 (46.6 KB)
wlan2 Link encap:Ethernet HWaddr 00:02:72:a7:06:97
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:41 errors:0 dropped:26 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13312 (13.3 KB) TX bytes:0 (0.0 B)
j@mydamncomputer:~$ sudo lshw -C network
[sudo] password for j:
*-network
description: Ethernet interface
product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 03
serial: 00:15:f2:a8:78:c2
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd
autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI
duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII
speed=10MB/s
resources: irq:20 memory:cfffe000-cfffefff ioport:e800(size=64)
*-network
description: Wireless interface
physical id: 1
logical name: wlan2
serial: 00:02:72:a7:06:97
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=802.11b/g/n ...
j@mydamncomputer:~$
mydamncomputer:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:15:f2:a8:78:c2
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:588 errors:0 dropped:0 overruns:0 frame:0
TX packets:588 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:46640 (46.6 KB) TX bytes:46640 (46.6 KB)
wlan2 Link encap:Ethernet HWaddr 00:02:72:a7:06:97
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:41 errors:0 dropped:26 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13312 (13.3 KB) TX bytes:0 (0.0 B)

---

### Post by mejbr2003 on 2012-03-16
here is iwconfig
@mydamncomputer:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan2 802.11b/g/n ... ESSID:"NETGEAR"
Mode:Managed Frequency=2.447 GHz Access Point: 00:22:3F:B5:89:26
Bit Rate=130 Mb/s
Retry min limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

