---
title: "Intermittent wireless connectivity with Release 9.04 (jaunty) on a Dell XPS M1530"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by bwolf1 on 2009-05-03
For starters. I apologize if this is an annoying amount of detail, but I did technical support for many years and came to appreciate detailed descriptions of issues when I was troubleshooting them for customers. I have searched through these forums and on google, and haven't found an instance of anyone else experiencing an issue quite like mine (although I found a few that were vaguely similar).

I have been having an issue with Release 9.04 (jaunty) on my Dell XPS M1530 where my wirless intermittently disconnects. I haven't been able to narrow down a cause (high bandwidth useage, etc.), so it seems random, although it may not actually be random. My wife's computer connects to the same wirless gateway via Windows XP and has no problems. I also have a desktop machine running Release 8.10 (intrepid) that has a wired connection to the same gateway, and it has no problems. Although I haven't spent a lot of time with my XPS 1530 connected to the gateway via a wire, I have never had the issue when it is connected via a wire.  The problem seems to be specific to my Dell XPS M1530 and specific to the wireless connection. The way I resolve the issue (temporarily) is by clicking on the network status icon in the upper bar on the right, near the clock, to bring up the list of available networks, then click on the Belkin_N_Wireless_6784C6 (which is how my wireless router shows up in the list). Another thing that is probably worth mentioning is that throughout the entire process of the wirless conecction going out, and me reconnecting it, it actually shows to be active the entire time when hovering the mouse over the network status icon in the upper bar, on the right, near the clock. The way that I know it is out is because I can't load any web pages or ping anything outside of my local network until I reconnect it (or reboot, of course).

The last time it happened I opened a terminal window right after I lost connectivity and did a dmesg | grep -i wlan. 

Here's the output below from running the dmesg | grep -i wlan:

> [   19.319294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.537463] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   20.539236] wlan0: authenticated
[   20.539241] wlan0: associate with AP 00:1c:df:67:84:c6
[   20.541913] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=3)
[   20.541918] wlan0: associated
[   20.543708] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.556260] wlan0: disassociating by local choice (reason=3)
[   28.388050] wlan0: deauthenticated
[   28.389947] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   28.392718] wlan0: authenticate with AP 00:1c:df:67:84:c6
[   28.392729] wlan0: authenticated
[   28.392734] wlan0: associate with AP 00:1c:df:67:84:c6
[   28.400082] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=3)
[   28.400087] wlan0: associated
[   31.005055] wlan0: no IPv6 routers present
[ 1282.353314] wlan0: disassociating by local choice (reason=3)
[ 1282.361281] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1282.363111] wlan0: authenticated
[ 1282.363119] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1282.365683] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 1282.365690] wlan0: associated
[ 1282.371302] wlan0: disassociating by local choice (reason=3)
[ 1320.691316] wlan0: deauthenticated
[ 1320.695409] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1320.697164] wlan0: authenticated
[ 1320.697173] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1320.702807] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 1320.702814] wlan0: associated
[ 1399.194185] wlan0: direct probe to AP 00:1c:df:67:84:c6 try 1
[ 1399.197784] wlan0: disassociating by local choice (reason=3)
[ 1399.199831] wlan0 direct probe responded
[ 1399.199835] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1399.201567] wlan0: authenticated
[ 1399.201570] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1399.204152] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 1399.204159] wlan0: associated
[ 1427.570519] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1427.572277] wlan0: authenticated
[ 1427.572286] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1427.577316] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1427.577335] wlan0: authenticated
[ 1427.577341] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1427.577359] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 1427.577365] wlan0: associated
[ 1430.465547] wlan0: disassociated
[ 1431.465668] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1431.664171] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1431.864080] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1432.064092] wlan0: association with AP 00:1c:df:67:84:c6 timed out
[ 1434.733693] wlan0: deauthenticated
[ 1434.735711] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1434.741865] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 1434.741896] wlan0: authenticated
[ 1434.741902] wlan0: associate with AP 00:1c:df:67:84:c6
[ 1434.746296] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 1434.746305] wlan0: associated
[ 2601.927620] wlan0: disassociating by local choice (reason=3)
[ 2601.939212] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 2601.946724] wlan0: authenticated
[ 2601.946734] wlan0: associate with AP 00:1c:df:67:84:c6
[ 2601.950338] wlan0: RX AssocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 2601.950345] wlan0: associated
[ 2601.952537] wlan0: disassociating by local choice (reason=3)
[ 2641.804261] wlan0: deauthenticated
[ 2641.807568] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 2641.810815] wlan0: authenticate with AP 00:1c:df:67:84:c6
[ 2641.810846] wlan0: authenticated
[ 2641.810852] wlan0: associate with AP 00:1c:df:67:84:c6
[ 2641.820059] wlan0: RX ReassocResp from 00:1c:df:67:84:c6 (capab=0x401 status=0 aid=1)
[ 2641.820068] wlan0: associated

---

### Post by bwolf1 on 2009-05-04
Here's some ifconfig output, captured during my most recent outage. Maybe this will be helpful.

> eth0      Link encap:Ethernet  HWaddr 00:23:ae:1b:fe:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9566 (9.5 KB)  TX bytes:9566 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d2:68:b1  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fed2:68b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7767922 (7.7 MB)  TX bytes:1595130 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-D2-68-B1-38-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)And here's ifconfig data from another time that the issue recently ocurred.

> eth0      Link encap:Ethernet  HWaddr 00:23:ae:1b:fe:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9372 (9.3 KB)  TX bytes:9372 (9.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d2:68:b1  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fed2:68b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5312859 (5.3 MB)  TX bytes:1128911 (1.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-D2-68-B1-38-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

