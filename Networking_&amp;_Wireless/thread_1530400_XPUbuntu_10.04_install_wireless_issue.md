---
title: "XP/Ubuntu 10.04 install wireless issue"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by binaurally on 2010-07-13
My wireless had been working properly when I had  10.04 installed on my Sony Vaio VGN FS810 laptop. I installed a new hard drive (Seagate 160gb)  then put windows XP on it, then installed Ubuntu 10.04 on it as well  using Wubi. I cannot get my wireless to to connect to a network on  either platform. The card (Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01))
 is functioning, it see's my network (which has  an excellent signal), I enter my key and it says acquiring network  address, then never connects.I should note that my wired connection  works fine and other laptops in the house are connecting via wireless to  the network w/o issue. I know there are hundreds of other posts on here  about similar problems, Ive gone through them all and cant seem to get  this resolved. here is some output for various commands that Ive seen  used in some of those posts.
 sudo lshw -C network:
 *-network:0
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: wlan0
       version: 01
       serial: 00:14:a4:6a:34:57
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical  wireless
       configuration: broadcast=yes driver=ath5k latency=168  maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:b0100000-b010ffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller  Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:ef:d5:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp  mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100  driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A  ip=192.168.1.125 latency=66 link=yes maxlatency=56 mingnt=8  multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:b0116000-b0116fff ioport:2000(size=64)
 ifconfig:
 eth0      Link encap:Ethernet  HWaddr 00:01:4a:ef:d5:f8
          inet addr:192.168.1.125  Bcast:192.168.1.255   Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:feef:d5f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100623312 (100.6 MB)  TX bytes:3161897 (3.1 MB)
 lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1904 (1.9 KB)  TX bytes:1904 (1.9 KB)
 wlan0     Link encap:Ethernet  HWaddr 00:14:a4:6a:34:57
          inet6 addr: fe80::214:a4ff:fe6a:3457/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1691 (1.6 KB)  TX bytes:6007 (6.0 KB)
  ifconfig:
 eth0      Link encap:Ethernet  HWaddr 00:01:4a:ef:d5:f8
          inet addr:192.168.1.125  Bcast:192.168.1.255   Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:feef:d5f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100623312 (100.6 MB)  TX bytes:3161897 (3.1 MB)
 lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1904 (1.9 KB)  TX bytes:1904 (1.9 KB)
 wlan0     Link encap:Ethernet  HWaddr 00:14:a4:6a:34:57
          inet6 addr: fe80::214:a4ff:fe6a:3457/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1691 (1.6 KB)  TX bytes:6007 (6.0 KB)
 binaurally@ubuntu:~$ iwconfig
lo        no wireless extensions.
 eth0      no wireless extensions.
 wlan0     IEEE 802.11bg  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"
          Mode:Managed  Frequency:2.437 GHz  Access Point:  Not-Associated
          Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


dmesg:


[  192.456086] wlan0: deauthenticating from 00:16:b6:27:19:11 by local choice (reason=3)
[  192.474939] wlan0: direct probe to AP 00:16:b6:27:19:11 (try 1)
[  192.477733] wlan0: direct probe responded
[  192.477741] wlan0: authenticate with AP 00:16:b6:27:19:11 (try 1)
[  192.480317] wlan0: authenticated
[  192.480349] wlan0: associate with AP 00:16:b6:27:19:11 (try 1)
[  192.482540] wlan0: RX AssocResp from 00:16:b6:27:19:11 (capab=0x411 status=0 aid=5)
[  192.482545] wlan0: associated
[  192.483425] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  202.872032] wlan0: no IPv6 routers present
[  202.997015] wlan0: deauthenticating from 00:16:b6:27:19:11 by local choice (reason=3)
[  214.816057] wlan0: Creating new IBSS network, BSSID 32:bb:04:fa:9c:83
[  215.895518] ip_tables: (C) 2000-2006 Netfilter Core Team
[  215.943446] nf_conntrack version 0.5.0 (15894 buckets, 63576 max)
[  215.945861] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  215.945868] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[  215.945871] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  216.100031] wlan0: no IPv6 routers present
[  289.816171] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[  289.816543] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  300.188034] eth0: no IPv6 routers present
[  434.181725] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
[  434.181731] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[  434.617060] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
[  434.617064] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[  438.021013] atkbd.c: Unknown key pressed (translated set 2, code 0xf5 on isa0060/serio0).
[  438.021019] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[  438.224263] atkbd.c: Unknown key released (translated set 2, code 0xf5 on isa0060/serio0).
[  438.224268] atkbd.c: Use 'setkeycodes e075 <keycode>' to make it known.
[ 1153.869585] wlan0: Trigger new scan to find an IBSS to join
[ 1162.504867] wlan0: Trigger new scan to find an IBSS to join
[ 1223.778971] wlan0: Trigger new scan to find an IBSS to join


 Thanks for your time, hope we can get this resolved!

---

