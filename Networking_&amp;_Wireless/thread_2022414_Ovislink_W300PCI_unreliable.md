---
title: "Ovislink W300PCI unreliable"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by ciri on 2012-07-10
I've been at this for quite a while, but I can't seem to figure out why my wireless card can't maintain a stable connection. Network Manager is telling me that I'm connected to the AP, even so, my connection is interrupted frequently. Here's a typical ping response showing the behavior:

```

64 bytes from 192.168.0.1: icmp_req=45 ttl=64 time=2.22 ms
64 bytes from 192.168.0.1: icmp_req=46 ttl=64 time=1.71 ms
64 bytes from 192.168.0.1: icmp_req=47 ttl=64 time=38.4 ms
64 bytes from 192.168.0.1: icmp_req=48 ttl=64 time=9.88 ms
64 bytes from 192.168.0.1: icmp_req=49 ttl=64 time=8.31 ms
64 bytes from 192.168.0.1: icmp_req=54 ttl=64 time=9.19 ms
64 bytes from 192.168.0.1: icmp_req=55 ttl=64 time=9.38 ms
64 bytes from 192.168.0.1: icmp_req=56 ttl=64 time=11.5 ms
64 bytes from 192.168.0.1: icmp_req=78 ttl=64 time=10.1 ms
64 bytes from 192.168.0.1: icmp_req=79 ttl=64 time=11.4 ms
64 bytes from 192.168.0.1: icmp_req=**161** ttl=64 time=11.2 ms
64 bytes from 192.168.0.1: icmp_req=162 ttl=64 time=9.45 ms
64 bytes from 192.168.0.1: icmp_req=163 ttl=64 time=8.40 ms
64 bytes from 192.168.0.1: icmp_req=164 ttl=64 time=11.9 ms

```

(after which it stopped pinging at all). A dmesg shows no useful information here:
```

[   34.256153] wlan0: authenticate with cc:b2:55:f3:b8:c8 (try 1)
[   34.258152] wlan0: authenticated
[   34.258311] wlan0: associate with cc:b2:55:f3:b8:c8 (try 1)
[   34.261767] wlan0: RX ReassocResp from cc:b2:55:f3:b8:c8 (capab=0xc21 status=0 aid=1)
[   34.261770] wlan0: associated
[   44.816003] wlan0: no IPv6 routers present

```
It stops there, note that I had disabled IPv6.

I'm using:
```

Ubuntu 12.04 LTS
3.2.0-26-generic-pae i686

```

My wireless card is an Ovislink W300PCI, but it seems to be detected as:
```

04:06.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R [1814:0701]

```

Some more info:
```

wlan0     Link encap:Ethernet  HWaddr 00:1d:1a:07:e5:6f  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:1aff:fe07:e56f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1348 (1.3 KB)  TX bytes:26158 (26.1 KB)

wlan0     IEEE 802.11bgn  ESSID:"xxx"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: CC:B2:55:F3:B8:C8   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  *-network               
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: wlan0
       version: 00
       serial: 00:1d:1a:07:e5:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-26-generic-pae firmware=0.29 ip=192.168.0.100 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fdde0000-fddeffff

```

```

$ iwlist scan
          Cell 01 - Address: CC:B2:55:F3:B8:C8
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005786ea347
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0005456E726963
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1605030400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000

```
The signal strength is certainly not outstanding, but could this be worsened due to driver problems? My other devices (also 801.11g devices) are able to connected without problems from the same distance to the AP.

Drivers:
```

xxx@yyy:~$ lsmod | grep rt
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
parport_pc             32114  1 
parport                40930  3 ppdev,parport_pc,lp

```

Based on other post I have tried shutting down the power-management behavior and blacklisting existing drivers (either 2800* or 2x000*). Furthermore I disabled the security temporarily since I noticed some people seem to be having trouble with WPA. None of those helped so I resorted to compiling/using the following drivers:
[LIST]
[*]rt2860sta
[*]rt3562sta
[/LIST]

Both with either the same result or worse. E.g.
```

ra0       Ralink STA  ESSID:"xxx"  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=62/100  Signal level:-72 dBm  Noise level:-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I don't have any other leads left so I'm hoping someone can point me in the right direction. Thank you in advance for your help!

---

