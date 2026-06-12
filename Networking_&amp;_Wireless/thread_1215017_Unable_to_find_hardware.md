---
title: "Unable to find hardware"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by feb3 on 2009-07-16
Using Ubuntu Jaunty dual-booting with Vista on a laptop with a wireless card that is not compatible with Linux - it is a SiS163u.
I have the ndiswrapper installed plus the 163u.inf file. 
When I use the Wireless utility it says that the driver is installed but is unable to find hardware.

I have run the following commands:

**Sudo ifconfig:**
eth0 Link encap:Ethernet HWaddr 00:03:0d:59:cb:39
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 Base address:0x2000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:56 errors:0 dropped:0 overruns:0 frame:0
TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3928 (3.9 KB) TX bytes:3928 (3.9 KB)
wlan0 Link encap:Ethernet HWaddr 00:1f:1f:3c:2c:e1
inet addr:192.168.1.66 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21f:1fff:fe3c:2ce1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:559 errors:0 dropped:0 overruns:0 frame:0
TX packets:531 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:426280 (426.2 KB) TX bytes:91565 (91.5 KB)
wmaster0 Link encap:UNSPEC HWaddr 00-1F-1F-3C-2C-E1-63-65-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

**iwconfig:**
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"Thomson520687"
Mode:Managed Frequency:2.412 GHz Access Point: 00:1F:9F:15:AB:AD
Bit Rate=1 Mb/s Tx-Power=10 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management:off
Link Quality=70/100 Signal level:-58 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.

**iwlist**
Usage: iwlist [interface] scanning [essid NNN] [last]
[interface] frequency
[interface] channel
[interface] bitrate
[interface] rate
[interface] encryption
[interface] keys
[interface] power
[interface] txpower
[interface] retry
[interface] ap
[interface] accesspoints
[interface] peers
[interface] event
[interface] auth
[interface] wpakeys
[interface] genie
[interface] modulation 

Currently using a USB dongle for wireless but would like to know if there is any chance at all that I might be able to get the one in the laptop working. Have researched this extensively but cannot find a solution so would be grateful if someone could advise.

---

### Post by nixscripter on 2009-07-29
Did you get the INF/SYS file from Vista or XP? ndiswrapper does not accept Vista drdivers.

---

