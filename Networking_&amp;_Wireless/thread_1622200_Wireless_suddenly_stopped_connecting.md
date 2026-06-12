---
title: "Wireless suddenly stopped connecting"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by jfd3220 on 2010-11-15
I have Ubuntu 10.04 installed on an EEE PC 1005HA.  I have installed an Intel 6200 wireless card.  I have been using it problem free for the past few months, but starting yesterday I can no longer connect to wireless networks, although I can see them and try to connect.  This is a significant problem for me because I am currently travelling in SE Asia.  I tried downloading the latest 10.10 Netbook Remix and making a bootable flash but I haven't been able to get it to boot, in spite of having tried Unetbootin, the windoze tool suggested on the ubuntu site, and the startup disk creator on my netbook.  Anyway, here is what I get after I try to connect to the unsecure network &#8220;linksys&#8221; using Network Manager.

```
sudo iwconfig
wlan0     IEEE 802.11abgn  ESSID:"\x02\x1A\xFEC\xFB\xFA\xAA:\xFB)\xD1\xE6\x05<|\x94u\xD8\xBEa\x89\xF9\\xBB\xA8\x99\x0F\x95\xB1\xEB\xF1\xB3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:on 
```

The ESSID has become garbage after disconnection, but I believe that was a previously reported bug.
When I try to connect to a network and then run dhclient this is what I get.

```
sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit https://www.isc.org/software/dhcp/ 

Listening on LPF/wlan0/00:23:14:28:b1:d0 
Sending on   LPF/wlan0/00:23:14:28:b1:d0 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
No DHCPOFFERS received. 
No working leases in persistent database &#8211; sleeping. 

```

This is from tail -100 /var/log/messages but the last bit is from 30 minutes before the last attempt to connect to a network

```
tail -100 /var/log/messages
Nov 15 18:13:55 (none) kernel: [ 1959.402528] Restarting tasks ... done. 
Nov 15 18:13:56 (none) kernel: [ 1960.501294] Registered led device: iwl-phy0::radio 
Nov 15 18:13:56 (none) kernel: [ 1960.502629] Registered led device: iwl-phy0::assoc 
Nov 15 18:13:56 (none) kernel: [ 1960.503975] Registered led device: iwl-phy0::RX 
Nov 15 18:13:56 (none) kernel: [ 1960.505045] Registered led device: iwl-phy0::TX 
Nov 15 18:13:56 (none) kernel: [ 1960.514524] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Nov 15 18:13:56 (none) kernel: [ 1960.524020] ADDRCONF(NETDEV_UP): eth0: link is not ready 
Nov 15 18:14:18 (none) kernel: [ 1982.301698] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

And this is what I get from dmesg.

```
sudo dmesg
[ 1962.216389] CPU1 attaching sched-domain: 
[ 1962.216398]  domain 0: span 0-1 level SIBLING 
[ 1962.216408]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589) 
[ 1962.216429]   domain 1: span 0-1 level MC 
[ 1962.216439]    groups: 0-1 (cpu_power = 1178) 
[ 1981.654307] wlan0: deauthenticating from 00:90:4c:91:00:01 by local choice (reason=3) 
[ 1981.695806] wlan0: direct probe to AP 00:90:4c:91:00:01 (try 1) 
[ 1981.892171] wlan0: direct probe to AP 00:90:4c:91:00:01 (try 2) 
[ 1981.894451] wlan0: direct probe responded 
[ 1981.894467] wlan0: authenticate with AP 00:90:4c:91:00:01 (try 1) 
[ 1982.092122] wlan0: authenticate with AP 00:90:4c:91:00:01 (try 2) 
[ 1982.094161] wlan0: authenticated 
[ 1982.094244] wlan0: associate with AP 00:90:4c:91:00:01 (try 1) 
[ 1982.296099] wlan0: associate with AP 00:90:4c:91:00:01 (try 2) 
[ 1982.298250] wlan0: RX AssocResp from 00:90:4c:91:00:01 (capab=0x401 status=0 aid=6) 
[ 1982.298265] wlan0: associated 
[ 1982.301698] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1993.032120] wlan0: no IPv6 routers present 
[ 2028.264578] wlan0: deauthenticating from 00:90:4c:91:00:01 by local choice (reason=3) 
[ 3558.215025] wlan0: deauthenticating from 00:90:4c:91:00:01 by local choice (reason=3) 
[ 3558.256449] wlan0: direct probe to AP 00:90:4c:91:00:01 (try 1) 
[ 3558.456123] wlan0: direct probe to AP 00:90:4c:91:00:01 (try 2) 
[ 3558.461993] wlan0: direct probe responded 
[ 3558.462015] wlan0: authenticate with AP 00:90:4c:91:00:01 (try 1) 
[ 3558.660122] wlan0: authenticate with AP 00:90:4c:91:00:01 (try 2) 
[ 3558.662172] wlan0: authenticated 
[ 3558.662279] wlan0: associate with AP 00:90:4c:91:00:01 (try 1) 
[ 3558.860131] wlan0: associate with AP 00:90:4c:91:00:01 (try 2) 
[ 3558.862852] wlan0: RX AssocResp from 00:90:4c:91:00:01 (capab=0x401 status=0 aid=6) 
[ 3558.862872] wlan0: associated 
[ 3604.261135] wlan0: deauthenticating from 00:90:4c:91:00:01 by local choice (reason=3) 

```

It seems to connect and then disconnect (deauthenticating by local choice (reason=3)). I think that's the problem.  I googled it and tried killing the wpa_supplicant process but that doesn't help. I also uninstalled network-manager and tried connecting manually but that didn't work either.  Currently I have reinstalled network-manager.

```
sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:0f:ce:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:49384 (49.3 KB)  TX bytes:49384 (49.3 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:23:14:28:b1:d0  
          inet6 addr: fe80::223:14ff:fe28:b1d0/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:47350 (47.3 KB)  TX bytes:16307 (16.3 KB) 

wlan0:avahi Link encap:Ethernet  HWaddr 00:23:14:28:b1:d0  
          inet addr:169.254.8.152  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 

```

The wlan0:avahi part only seems to show up after I attempt to connect to a network.
Any help would be much appreciated.

EDIT
This bug has a bunch of suggestions but none of them have seemed to fix the problem [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992).  Using a static IP is obviously not an option if I am travelling.
I tried undoing everything I did and now it won't even authenticate so in dmesg I get

wlan0: direct probe to AP XXXX (try 1)
wlan0: direct probe to AP XXXX (try 2)
wlan0: direct probe to AP XXXX (try 3)
wlan0: direct probe to AP XXXX (timed out)

Great.

---

