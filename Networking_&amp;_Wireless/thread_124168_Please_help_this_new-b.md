---
title: "Please help this new-b"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by elp on 2006-01-31
I have a laptop compaq presario R3220US.
I can connect to SBC-YAHOO dsl (2wire.com) thru. wire.
When I try to use my wireless Linksys wpc54gs with speed booster does not connect.
using ndiswrapper it shows the wireless is loaded when I go to system, adminstration and network. 
iwconfig shows:
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
---------------------------------
elp7@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:09:08:78
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8282994 (7.8 MiB)  TX bytes:454638 (443.9 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1335050 (1.2 MiB)  TX bytes:1335050 (1.2 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:5F:77:47
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:d0200000-d0201fff

according to Windows XP
ssid: 2wire966
ip 192.168.1.67
subnet: 255.255.255.0
gateway: 192.168.1.254
DNA: 192.168.1.254
mac adrs: 00-14-95-41-43-9A
channel:6
thanks.......................

---

### Post by jasmuz on 2006-02-01
did you try loading your wireless connection with dhclient?

---

