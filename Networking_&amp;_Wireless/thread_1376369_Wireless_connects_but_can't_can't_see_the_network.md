---
title: "Wireless connects but can't can't see the network"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by mrlukeh on 2010-01-09
I've got a Zotac MAG HD-ND01 with XBMC live installed. This is built on Karmic Koala and runs very nicely through the wired NIC. 

I configure the box using a cable. I'm using WPA2-PSK and it is clearly authenticating OK.. It gets an IP address.. the AP shows a connection to the box. My XP laptop connects to the access point OK.. just can't connect to the box via the wireless, and it can't see the network using wireless.

I have followed a number of threads on connecting Atheros 9XXX wireless ([http://ubuntuforums.org/showthread.php?t=894177](http://ubuntuforums.org/showthread.php?t=894177), [http://ubuntuforums.org/showthread.php?t=1309605](http://ubuntuforums.org/showthread.php?t=1309605), [http://ubuntuforums.org/showthread.php?t=930667](http://ubuntuforums.org/showthread.php?t=930667)) but no joy. 

Any ideas? Also, can Ubuntu connect to the AP at any speed greater than 54MB? My windows PC connects at 144MB+ . Will ndiswrappers connect at those sorts of speeds?

lspci -nn

[INDENT]04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
[/INDENT]

iwconfig

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AV"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:C6:CC:FD:A8
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]

ifconfig
[INDENT]wlan0     Link encap:Ethernet  HWaddr 00:25:d3:c2:9b:3d
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fec2:9b3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:342468 (342.4 KB)  TX bytes:3378 (3.3 KB)
[/INDENT]
dmesg | grep wlan0


[   15.879251] wlan0: deauthenticating from 00:1f:c6:cc:fd:a8 by local choice (reason=3)
[   15.879333] wlan0: direct probe to AP 00:1f:c6:cc:fd:a8 (try 1)
[   15.885186] wlan0: direct probe responded
[   15.885194] wlan0: authenticate with AP 00:1f:c6:cc:fd:a8 (try 1)
[   15.887177] wlan0: authenticated
[   15.887223] wlan0: associate with AP 00:1f:c6:cc:fd:a8 (try 1)
[   15.891188] wlan0: RX AssocResp from 00:1f:c6:cc:fd:a8 (capab=0x431 status=0 aid=1)
[   15.891195] wlan0: associated
[   15.891967] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.128013] wlan0: no IPv6 routers present

---

### Post by poikiloid on 2011-06-15
did you ever find a solution? I just purchased the same computer, with XBMC live also, and while wicd-curses shows I am connected to wireless, when I log out and back in (into XBMC Live), XBMC says I am not connected. I am dual booted with Ubuntu 11.04, which connects to the wireless fine...

---

