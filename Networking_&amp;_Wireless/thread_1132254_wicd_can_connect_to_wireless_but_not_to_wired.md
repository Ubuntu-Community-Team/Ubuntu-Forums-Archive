---
title: "wicd can connect to wireless but not to wired"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by kartoffsky on 2009-04-21
**SOLVED**???

-swapped out the router and all is well-

I can use wicd to connect to one wired network (in Brooklyn) and many wireless connections (all over) but can't complete wired connection in my new place. And I just tacked white CAT5-E cable everywhere. Very sad.

Ubuntu 8.10 Dell Latitude D510

Wired connection: Netgear switch ->cable modem from Time Warner Cable (New York City)

Roommates's Mac connects no problem - no password, no static IP

Wicd works in as much as it connects to (other people's faint) wireless connections. When I plug it into cable modem (or switch) it sees it but on connection attempt it hangs, "Obtaining IP address...", until it eventually quits.

I don't know what sort of diagnostic things to post here other than **ifconfig** and **dmesg|grep eth** (see below). I look forward to anyone's help because I can't do my work. Thank you!

somename@Somecomputer:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr (CENSORED) 
          inet6 addr: fe80::215:c5ff:fe10:d6a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27493705 (27.4 MB)  TX bytes:37512 (37.5 KB)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr (CENSORED)   
          inet addr:169.254.8.117  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1668 (1.6 KB)  TX bytes:1668 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr (CENSORED) 
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe41:9035/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6978421 (6.9 MB)  TX bytes:718617 (718.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr (CENSORED) -33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
someone@Somecomputer:~$** dmesg|grep eth**
[    3.752415] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet (CENSORED) 
[    4.290807] Driver 'sd' needs updating - please use bus_type methods
[    4.293096]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   32.862146] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.816199] b44: eth0: Link is up at 100 Mbps, full duplex.
[   35.816204] b44: eth0: Flow control is off for TX and off for RX.
[   35.816896] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   46.640034] eth0: no IPv6 routers present
[ 1178.636811] b44: eth0: powering down PHY
[ 1179.056609] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1182.000203] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1182.000214] b44: eth0: Flow control is off for TX and off for RX.
[ 1182.002703] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1192.224168] eth0: no IPv6 routers present
[36414.204242] b44: eth0: powering down PHY
[36414.489501] ADDRCONF(NETDEV_UP): eth0: link is not ready
[36418.000343] b44: eth0: Link is up at 100 Mbps, full duplex.
[36418.000354] b44: eth0: Flow control is off for TX and off for RX.
[36418.002848] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[36428.104028] eth0: no IPv6 routers present
[37798.374125] eth0: late interrupt.
[37798.392209] b44: eth0: powering down PHY
[37798.798626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[37802.000348] b44: eth0: Link is up at 100 Mbps, full duplex.
[37802.000358] b44: eth0: Flow control is off for TX and off for RX.
[37802.002868] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[37812.648164] eth0: no IPv6 routers present
[37933.960223] b44: eth0: powering down PHY
[37934.283297] ADDRCONF(NETDEV_UP): eth0: link is not ready
[37938.000342] b44: eth0: Link is up at 100 Mbps, full duplex.
[37938.000352] b44: eth0: Flow control is off for TX and off for RX.
[37938.002888] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[37948.864027] eth0: no IPv6 routers present
[38035.440238] b44: eth0: powering down PHY
[38035.747467] ADDRCONF(NETDEV_UP): eth0: link is not ready
[38039.000344] b44: eth0: Link is up at 100 Mbps, full duplex.
[38039.000355] b44: eth0: Flow control is off for TX and off for RX.
[38039.002895] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[38049.512172] eth0: no IPv6 routers present
[38115.804243] b44: eth0: powering down PHY
[38116.087705] ADDRCONF(NETDEV_UP): eth0: link is not ready
[38119.000344] b44: eth0: Link is up at 100 Mbps, full duplex.
[38119.000355] b44: eth0: Flow control is off for TX and off for RX.
[38119.002862] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[38129.092167] eth0: no IPv6 routers present
[38436.838829] eth0: late interrupt.
[38436.844210] b44: eth0: powering down PHY
[38437.117946] ADDRCONF(NETDEV_UP): eth0: link is not ready
[38440.000346] b44: eth0: Link is up at 100 Mbps, full duplex.
[38440.000356] b44: eth0: Flow control is off for TX and off for RX.
[38440.002859] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[38450.468173] eth0: no IPv6 routers present
[38537.795434] b44: eth0: powering down PHY
[38538.084074] ADDRCONF(NETDEV_UP): eth0: link is not ready
[38541.000343] b44: eth0: Link is up at 100 Mbps, full duplex.
[38541.000354] b44: eth0: Flow control is off for TX and off for RX.
[38541.002888] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[38551.464033] eth0: no IPv6 routers present

---

