---
title: "Netgear WG111v2 (USB) DHCP(?) issues with Karmic"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Chris-Chicken on 2010-01-29
Hi Everyone, having some frustrating issues getting the WG111v2 usb dongle to work with Karmic NBR. Using an HP mini 1030NR. 

I have tried Wicd, Ndiswrapper (with various drivers) and the native RTL8187 driver. Can always see the APs and connect, obtain an IP address, and see the AP's MAC..... but I'm never able to download any information... the connection just hangs. 

The internal card (Broadcom 4312) works fine. Other people report that the WG11v2 works out of the box with Karmic.

I've lost the receipt..... :O

There is no security on the AP.

Here's some terminal output.....

IWconfig

```
wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:E4:27:4C   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
 
dmesg

```
cwis2phar@Sylvan-Manko:~$ dmesg | grep "wlan0"
[   65.834203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.726587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.973488] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   91.973698] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   91.978084] wlan0: authenticated
[   91.978104] wlan0: associate with AP 00:0f:b5:e4:27:4c
[   91.981339] wlan0: deauthenticated (Reason: 6)
[   92.980126] wlan0: direct probe to AP 00:0f:b5:e4:27:4c try 1
[   92.983749] wlan0 direct probe responded
[   92.983766] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   92.986086] wlan0: authenticated
[   92.986107] wlan0: associate with AP 00:0f:b5:e4:27:4c
[   92.989021] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=11)
[   92.989041] wlan0: associated
[   92.995511] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.112063] wlan0: no IPv6 routers present
[  300.321104] wlan0: no probe response from AP 00:0f:b5:e4:27:4c - disassociating
[  309.359148] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  311.787368] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[  311.789848] wlan0: authenticated
[  311.789859] wlan0: associate with AP 00:0f:b5:e4:27:4c
[  311.792140] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=11)
[  311.792155] wlan0: associated
[  311.797251] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  322.264068] wlan0: no IPv6 routers present
[  729.630621] wlan0: no probe response from AP 00:0f:b5:e4:27:4c - disassociating
[ 1546.114546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1548.525675] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[ 1548.528749] wlan0: authenticated
[ 1548.528769] wlan0: associate with AP 00:0f:b5:e4:27:4c
[ 1548.531072] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=6)
[ 1548.531088] wlan0: associated
[ 1548.538911] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1558.760081] Hi Everyone, having some frustrating issues getting the WG111v2 usb dongle to work with Karmic NBR. Using an HP mini 1030NR. 

I have tried Wicd, Ndiswrapper (with various drivers) and the native RTL8187 driver. Can always see the APs and connect, obtain an IP address, and see the AP's MAC..... but I'm never able to download any information... the connection just hangs. 

The internal card (Broadcom 4312) works fine. Other people report that the WG11v2 works out of the box with Karmic.

I've lost the receipt..... :O

There is no security on the AP.

Here's some terminal output.....

IWconfig

[CODE]wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:E4:27:4C   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
 
dmesg

```
cwis2phar@Sylvan-Manko:~$ dmesg | grep "wlan0"
[   65.834203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.726587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.973488] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   91.973698] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   91.978084] wlan0: authenticated
[   91.978104] wlan0: associate with AP 00:0f:b5:e4:27:4c
[   91.981339] wlan0: deauthenticated (Reason: 6)
[   92.980126] wlan0: direct probe to AP 00:0f:b5:e4:27:4c try 1
[   92.983749] wlan0 direct probe responded
[   92.983766] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[   92.986086] wlan0: authenticated
[   92.986107] wlan0: associate with AP 00:0f:b5:e4:27:4c
[   92.989021] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=11)
[   92.989041] wlan0: associated
[   92.995511] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.112063] wlan0: no IPv6 routers present
[  300.321104] wlan0: no probe response from AP 00:0f:b5:e4:27:4c - disassociating
[  309.359148] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  311.787368] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[  311.789848] wlan0: authenticated
[  311.789859] wlan0: associate with AP 00:0f:b5:e4:27:4c
[  311.792140] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=11)
[  311.792155] wlan0: associated
[  311.797251] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  322.264068] wlan0: no IPv6 routers present
[  729.630621] wlan0: no probe response from AP 00:0f:b5:e4:27:4c - disassociating
[ 1546.114546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1548.525675] wlan0: authenticate with AP 00:0f:b5:e4:27:4c
[ 1548.528749] wlan0: authenticated
[ 1548.528769] wlan0: associate with AP 00:0f:b5:e4:27:4c
[ 1548.531072] wlan0: RX AssocResp from 00:0f:b5:e4:27:4c (capab=0x421 status=0 aid=6)
[ 1548.531088] wlan0: associated
[ 1548.538911] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1558.760081] wlan0: no IPv6 routers present

```

iwlist scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E4:27:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026bff7998b
                    Extra: Last beacon: 62612ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD1A00037F0301000000000FB5E4274C020FB5E4274C64002C011F08

```

Some output for DHCLIENT 

```
There is already a pid file /var/run/dhclient.pid with pid 4680
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:33:7b:51:4d
Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.8 from 192.168.1.1
bound to 192.168.1.8 -- renewal in 35798 seconds.

```

If I repeat the command, the connection is often dropped as I press return, and we get this:

```
There is already a pid file /var/run/dhclient.pid with pid 4773
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:33:7b:51:4d
Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.8
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Now, even when the DHCP packets were being returned, there was no joy with the net. GoogleChat reported it was connecting, but eventually just timed out.



If anyone has the slightest idea what is going on here, I would be very much indebted to you. And your karma will no doubt benefit :)

Thanks,

Chris.
[/CODE]

iwlist scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E4:27:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026bff7998b
                    Extra: Last beacon: 62612ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD1A00037F0301000000000FB5E4274C020FB5E4274C64002C011F08

```

Some output for DHCLIENT 

```
There is already a pid file /var/run/dhclient.pid with pid 4680
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:33:7b:51:4d
Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.8 from 192.168.1.1
bound to 192.168.1.8 -- renewal in 35798 seconds.

```

If I repeat the command, the connection is often dropped as I press return, and we get this:

```
There is already a pid file /var/run/dhclient.pid with pid 4773
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:33:7b:51:4d
Sending on   LPF/wlan0/00:1f:33:7b:51:4d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.8
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Now, even when the DHCP packets were being returned, there was no joy with the net. GoogleChat reported it was connecting, but eventually just timed out.


If anyone has the slightest idea what is going on here, I would be very much indebted to you. And your karma will no doubt benefit :)

Thanks,

Chris.

---

### Post by Chris-Chicken on 2010-01-30
<<Bump!>>

I notice that in the above code, the dongle is saying that there are "no IPv6 routers present"

Not sure if it's set to only look for these... or even the exact nature of v6 and v4....

Isn't there anyone with any ideas here?

Thanks again in advance,

Chris.

:KS

---

### Post by travmon69 on 2010-01-30
yes i use wg111v2 on karmic works.  i  noticed  that  i need to  leave it unplugged till  ubuntu boots then plugin  the  usb adapter.

---

### Post by Chris-Chicken on 2010-01-31
I've just tried to run the latest standard Ubuntu release (Lucid) from a live USB - and the same problem occurs, so it isn't a UNR issue.

Any takers or suggestions at this point would be ..... I'm not sure a suitable word exists. :D

---

