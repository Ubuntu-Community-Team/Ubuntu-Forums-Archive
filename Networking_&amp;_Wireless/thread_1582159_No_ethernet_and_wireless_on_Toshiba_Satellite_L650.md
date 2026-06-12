---
title: "No ethernet and wireless on Toshiba Satellite L650 C13"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by Inoki on 2010-09-26
Hi lads,

I got a very odd problem, I cannot access the internet except for my mobile broadband using Sony Ericsson, because my ethernet doesn't get recognized and wireless although it says it's connected, it doesn't receive any signal.

I tried this fix [http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html) but didn't help (sixth post from top) and also scrolled lower for the wireless fix, didn't work. Can anybody help me here?

I got a Toshiba Satellite L650 C13. I'm using Linux Mint 9 64 bit, which is a derivative of Ubuntu as you know, so any solution you provide should apply.

For wired:

```
Network: Card-1 Realtek Device 8172 driver rtl819xSE
Card-2 Atheros AR8152 v1.1 Fast Ethernet
~ $ iwconfig
lo no wireless extensions.

wlan0 802.11bgn Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.457 GHz Access Point: Not-Associated 
Bit Rate:300 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management:off
Link Quality=10/100 Signal level=0 dBm Noise level=-100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

usb0 no wireless extensions.

ppp0 no wireless extensions.
```

For wireless:

```
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo* * * * no wireless extensions.

wlan0* * *802.11bgn* Nickname:"rtl8191SEVA2"
* * * * * Mode:Managed* Frequency=2.457 GHz* Access Point: Not-Associated* *
* * * * * Bit Rate:300 Mb/s* *
* * * * * Retry:on* *RTS thr:off* *Fragment thr:off
* * * * * Encryption key:off
* * * * * Power Management:off
* * * * * Link Quality=10/100* Signal level=0 dBm* Noise level=-100 dBm
* * * * * Rx invalid nwid:0* Rx invalid crypt:0* Rx invalid frag:0
* * * * * Tx excessive retries:0* Invalid misc:0* *Missed beacon:0

usb0* * * no wireless extensions.

ppp0* * * no wireless extensions.

-------------------------
* IV. querying ifconfig...
lo* * * * Link encap:Local Loopback* 
* * * * * inet addr:127.0.0.1* Mask:255.0.0.0
* * * * * inet6 addr: ::1/128 Scope:Host
* * * * * UP LOOPBACK RUNNING* MTU:16436* Metric:1
* * * * * RX packets:1550 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:1550 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:0 
* * * * * RX bytes:60780 (60.7 KB)* TX bytes:60780 (60.7 KB)

ppp0* * * Link encap:Point-to-Point Protocol* 
* * * * * inet addr:91.191.83.6* P-t-P:10.64.64.64* Mask:255.255.255.255
* * * * * UP POINTOPOINT RUNNING NOARP MULTICAST* MTU:1500* Metric:1
* * * * * RX packets:52350 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:36499 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:3 
* * * * * RX bytes:72317302 (72.3 MB)* TX bytes:2390153 (2.3 MB)

usb0* * * Link encap:Ethernet* HWaddr 02:80:37:05:03:00* 
* * * * * inet6 addr: fe80::80:37ff:fe05:300/64 Scope:Link
* * * * * UP BROADCAST MULTICAST* MTU:1500* Metric:1
* * * * * RX packets:0 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:1000 
* * * * * RX bytes:0 (0.0 B)* TX bytes:0 (0.0 B)

wlan0* * *Link encap:Ethernet* HWaddr b4:82:fe:bd:63:26* 
* * * * * UP BROADCAST MULTICAST* MTU:1500* Metric:1
* * * * * RX packets:0 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:1000 
* * * * * RX bytes:0 (0.0 B)* TX bytes:0 (0.0 B)
* * * * * Interrupt:17 Memory:ffffc900050f0000-ffffc900050f0100 

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/usb0/02:80:37:05:03:00
Sending on* *LPF/usb0/02:80:37:05:03:00
Listening on LPF/wlan0/b4:82:fe:bd:63:26
Sending on* *LPF/wlan0/b4:82:fe:bd:63:26
Sending on* *Socket/fallback
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
-------------------------
* VI. querying nslookup google.com...
Server:* ** *160.218.43.200
Address:* *160.218.43.200#53

Non-authoritative answer:
Name:* *google.com
Address: 74.125.39.99
Name:* *google.com
Address: 74.125.39.103
Name:* *google.com
Address: 74.125.39.104
Name:* *google.com
Address: 74.125.39.105
Name:* *google.com
Address: 74.125.39.106
Name:* *google.com
Address: 74.125.39.147
```

---

### Post by Peter09 on 2010-09-26
Initially, as a first try, power your router Off/On to reset it, sometimes these things get messed up and don't work properly.

---

### Post by Inoki on 2010-09-26
Tried, didn't work. I know the problem is with the drivers on my laptop. Since they are new the Ubuntu team didn't compile any as of yet. I hope this will be done very soon, otherwise I'm cut off the internet and really wouldn't want to revert back to Windows.

Any solution?

---

### Post by Inoki on 2010-09-27
I was now advised to try inserting the commands in terminal one by one, instead of copy / pasting the whole thing.

Will post the results here.

---

### Post by Inoki on 2010-09-27
I finally got it working. The problem was I didn't insert the code one by one. After I did everything worked flawlessly :)

---

