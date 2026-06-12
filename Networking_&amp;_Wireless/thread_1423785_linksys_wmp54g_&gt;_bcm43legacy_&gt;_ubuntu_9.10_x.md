---
title: "linksys wmp54g &gt; bcm43legacy &gt; ubuntu 9.10 x64"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by basher2010 on 2010-03-07
i have searched all over and i see that this is an issue because people are still seeing problems.
i write this in the hopes a fortnights work will not be in vain.
please help.

lspci -nn

07:07.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"red alert"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

eth0      Link encap:Ethernet  HWaddr MAC ADDRESS  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe59:d935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5393 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:5202180 (5.2 MB)  TX bytes:576903 (576.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7876 (7.8 KB)  TX bytes:7876 (7.8 KB)

with sudo ifconfig wlan0 up i get :

wlan0     Link encap:Ethernet  HWaddr MAC   
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5537 (5.5 KB)  TX bytes:14994 (14.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-06-25-4A-4B-6D-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwlist scan (after various attempts, of not seeing my id)

Cell 06 - Address: AP MAC
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"red alert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005136a316
                    Extra: Last beacon: 350ms ago
                    IE: Unknown: 000972656420616C657274
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F

lsmod (only related to the specific driver)

b43legacy             133576  0 
mac80211              210040  1 b43legacy
cfg80211              109144  2 b43legacy,mac80211
led_class               5256  1 b43legacy
ssb                    41072  1 b43legacy

dmesg

[ 2892.330077] wlan0: direct probe to AP 00:24:01:69:3e:3e try 1
[ 2892.530018] wlan0: direct probe to AP 00:24:01:69:3e:3e try 2
[ 2892.730018] wlan0: direct probe to AP 00:24:01:69:3e:3e try 3
[ 2892.930016] wlan0: direct probe to AP 00:24:01:69:3e:3e timed out


hardware drivers > b43legacy is activated
network manager shows disconnected wlan0 and will not connect.

if i sudo dhclient wlan0

There is already a pid file /var/run/dhclient.pid with pid 2449
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:25:4a:4b:6d
Sending on   LPF/wlan0/00:06:25:4a:4b:6d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.353/0.353/0.353/0.000 ms
bound: renewal in 224941 seconds.

then i assume i would sudo ifconfig eth0 down 
but i get no internet access.

what am i missing? 
that recorded lease it mentions, is what i have the router configured to lease this mac.
192.168.0.100 belongs to the wlan0 in router settings.
also it seems i have to start from the beginning upon every reboot.
is there a way to save these settings of wlan0?
my intention is to take the system downstairs while the router remains upstairs connected to another system
i need the wireless to work.
anyones help is much appreciated as this is getting frustrating.

---

### Post by basher2010 on 2010-03-12
well no one has answered so i will answer this issue myself hoping it will benefit someone.

the issue was the hardware itself.
wmp54g version anything lower than 3 is simply not compatible with karmic.
i instead purchased this card for 25 bucks from frys.

[http://www.frys.com/product/5679631?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/5679631?site=sr:SEARCH:MAIN_RSLT_PG)

TRENDnet TEW-423PI 54Mbps Wireless G PCI Adapter 

i also looked the compatibility list over.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By) Manufacturer

currently the box is downstairs, but the reception is relative.
it only gets 16%.

i will resolve that issue, as well.

---

