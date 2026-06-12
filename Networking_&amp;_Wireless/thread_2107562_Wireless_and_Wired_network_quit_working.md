---
title: "Wireless and Wired network quit working"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by dch921 on 2013-01-22
Currently running 12.10 64 bit with 3.8rc4 kernel on Asus U56E laptop.

Wireless has been working fine for over a month now, and as of today booted up and wireless and wired networks will not connect. Keep receiving error "Connection Failed Acitvation of network connection failed" when trying to connect to wireless. When plugging in a wired connection just sits on connecting.

Tried rebooting several times, tried booting with an earlier kernel all with the same issues.

I was able to get internet connection with usb tethering from my phone this worked without having to do anything.

I have been through the forums and don't see an issue like this. Here are the results of several commands that might make sense to someone who knows more then I do. Any help would be great.

Thanks

```
don@Asus-Laptop:~$ uname -mr
3.8.0-030800rc4-generic x86_64
don@Asus-Laptop:~$ 
```

```
don@Asus-Laptop:~$ sudo lshw -C network
[sudo] password for don: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:d6:94:20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-030800rc4-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 10:bf:48:12:c9:43
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:dd400000-dd43ffff ioport:a000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 64:d4:da:70:19:a5
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no
```

```
don@Asus-Laptop:~$ dmesg | grep 'wlan'
[   15.349570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.616836] wlan0: authenticate with 00:18:f8:bf:e8:5c
[   16.622651] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[   16.624442] wlan0: authenticated
[   16.624633] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   16.624637] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   16.625521] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[   16.627704] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[   16.632137] wlan0: associated
[   16.632190] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.157203] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[   65.272237] wlan0: authenticate with 00:18:f8:bf:e8:5c
[   65.274634] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[   65.276444] wlan0: authenticated
[   65.276637] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   65.276641] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   65.278623] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[   65.280848] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[   65.283733] wlan0: associated
[  111.095502] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  114.283965] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  114.286236] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  114.288988] wlan0: authenticated
[  114.289337] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  114.289349] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  114.291204] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  114.293438] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  114.296886] wlan0: associated
[  160.034378] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  163.249275] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  163.251712] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  163.254509] wlan0: authenticated
[  163.254800] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  163.254814] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  163.255849] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  163.258292] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  163.261396] wlan0: associated
[  208.965662] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  508.815015] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  508.817424] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  508.820251] wlan0: authenticated
[  508.820599] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  508.820611] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  508.820772] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  508.823178] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  508.826100] wlan0: associated
[  554.523177] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  557.699447] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  557.701702] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  557.704568] wlan0: authenticated
[  557.704828] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  557.704841] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  557.705504] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  557.707797] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  557.710579] wlan0: associated
[  603.458486] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  606.707739] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  606.710165] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  606.713052] wlan0: authenticated
[  606.713339] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  606.713353] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  606.714105] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  606.716343] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  606.719238] wlan0: associated
[  652.392206] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[  655.570718] wlan0: authenticate with 00:18:f8:bf:e8:5c
[  655.573199] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[  655.575076] wlan0: authenticated
[  655.575549] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  655.575562] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  655.578905] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[  655.581206] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[  655.584111] wlan0: associated
[  701.330079] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1001.136584] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1001.139033] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1001.140810] wlan0: authenticated
[ 1001.140919] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1001.140923] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1001.143770] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1001.146050] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1001.149013] wlan0: associated
[ 1046.888095] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1050.123166] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1050.125615] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1050.128524] wlan0: authenticated
[ 1050.128834] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1050.128846] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1050.132445] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1050.134683] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1050.137589] wlan0: associated
[ 1095.818970] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1104.347158] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1104.349432] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1104.352318] wlan0: authenticated
[ 1104.353740] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1104.353752] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1104.354253] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1104.356510] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1104.359370] wlan0: associated
[ 1149.749853] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1152.924886] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1152.927288] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1152.930310] wlan0: authenticated
[ 1152.930643] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1152.930657] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1152.931430] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1152.933845] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1152.936848] wlan0: associated
[ 1198.687681] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1498.490821] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1498.493288] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1498.496160] wlan0: authenticated
[ 1498.496486] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1498.496499] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1498.496511] wlan0: waiting for beacon from 00:18:f8:bf:e8:5c
[ 1498.540289] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1498.542694] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1498.545561] wlan0: associated
[ 1544.244718] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1547.477697] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1547.480082] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1547.482239] wlan0: authenticated
[ 1547.482671] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1547.482684] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1547.484954] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1547.487344] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1547.490546] wlan0: associated
[ 1593.179367] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1596.361788] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1596.364069] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1596.367071] wlan0: authenticated
[ 1596.367403] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1596.367418] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1596.369689] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1596.372051] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1596.374951] wlan0: associated
[ 1642.112077] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1645.326994] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1645.329299] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1645.331117] wlan0: authenticated
[ 1645.331412] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1645.331427] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1645.334344] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1645.336762] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1645.339868] wlan0: associated
[ 1691.050403] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 1715.986697] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1788.217587] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 1788.221731] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 1788.224648] wlan0: authenticated
[ 1788.224957] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1788.224972] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1788.225471] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 1788.227699] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 1788.230498] wlan0: associated
[ 1788.230571] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1833.866685] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 2107.888252] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 2107.890545] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 2107.893488] wlan0: authenticated
[ 2107.893797] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2107.893811] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2107.895914] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 2107.898190] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 2107.901197] wlan0: associated
[ 2153.447712] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 2156.670244] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 2156.672659] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 2156.675500] wlan0: authenticated
[ 2156.675763] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2156.675777] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2156.676767] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 2156.679055] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 2156.681890] wlan0: associated
[ 2202.390537] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 2205.637684] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 2205.640004] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 2205.642836] wlan0: authenticated
[ 2205.643099] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2205.643108] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2205.645417] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 2205.647683] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 2205.650674] wlan0: associated
[ 2251.328799] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
[ 2254.541594] wlan0: authenticate with 00:18:f8:bf:e8:5c
[ 2254.544033] wlan0: send auth to 00:18:f8:bf:e8:5c (try 1/3)
[ 2254.546932] wlan0: authenticated
[ 2254.547290] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2254.547303] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2254.550274] wlan0: associate with 00:18:f8:bf:e8:5c (try 1/3)
[ 2254.552653] wlan0: RX AssocResp from 00:18:f8:bf:e8:5c (capab=0x401 status=0 aid=1)
[ 2254.555761] wlan0: associated
[ 2300.261311] wlan0: deauthenticating from 00:18:f8:bf:e8:5c by local choice (reason=3)
```


```
don@Asus-Laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
don@Asus-Laptop:~$ 
```

```
don@Asus-Laptop:~$ iwconfig
wmx0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
don@Asus-Laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            61749  1 
ip6table_filter        12815  0 
ip6_tables             27502  1 ip6table_filter
ebtable_nat            12807  0 
ebtables               30994  1 ebtable_nat
ipt_MASQUERADE         12759  3 
iptable_nat            12909  1 
nf_nat_ipv4            13316  1 iptable_nat
nf_nat                 26157  3 ipt_MASQUERADE,iptable_nat,nf_nat_ipv4
nf_conntrack_ipv4      14538  2 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  1 
nf_conntrack           83947  6 ipt_MASQUERADE,iptable_nat,nf_nat_ipv4,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  2 
xt_CHECKSUM            12549  1 
iptable_mangle         12734  1 
xt_tcpudp              12603  5 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29891  11 ip6table_filter,ip6_tables,ebtables,ipt_MASQUERADE,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
bridge                101039  0 
stp                    12976  1 bridge
llc                    14597  2 bridge,stp
rfcomm                 47864  0 
bnep                   18258  2 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             246934  10 rfcomm,bnep
coretemp               13596  0 
snd_hda_codec_hdmi     37223  1 
snd_hda_codec_realtek    79916  1 
uvcvideo               82214  0 
kvm_intel             137899  0 
snd_hda_intel          44347  3 
snd_hda_codec         141461  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12573  2 
videobuf2_core         40785  1 uvcvideo
iwldvm                249055  0 
kvm                   451836  1 kvm_intel
i2400m_usb             36542  0 
videodev              130053  2 uvcvideo,videobuf2_core
i2400m                107845  1 i2400m_usb
snd_hwdep              17764  1 snd_hda_codec
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
wimax                  34638  1 i2400m
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30749  1 snd_seq_midi
mac80211              613116  1 iwldvm
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17613  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
snd_timer              29989  2 snd_pcm,snd_seq
i915                  616209  4 
iwlwifi               183399  1 iwldvm
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
aes_x86_64             17255  1 aesni_intel
drm_kms_helper         49597  1 i915
cfg80211              525244  3 iwldvm,mac80211,iwlwifi
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
drm                   286915  5 i915,drm_kms_helper
psmouse                92375  0 
snd                    83673  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41820  0 
asus_nb_wmi            12854  0 
i2c_algo_bit           13564  1 i915
asus_wmi               24581  1 asus_nb_wmi
mac_hid                13253  0 
serio_raw              13215  0 
sparse_keymap          13890  1 asus_wmi
soundcore              15091  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                17144  0 
wmi                    19256  1 asus_wmi
microcode              23017  0 
video                  19467  2 i915,asus_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   101262  2 hid_generic,usbhid
atl1c                  41885  0 
don@Asus-Laptop:~$ 

```

---

### Post by sdowney717 on 2013-01-22
Laptops tend to have a hardware on-off switch to disable networking, maybe it is slid to off position

---

### Post by dch921 on 2013-01-22
No hardware buttons on the laptop for network connections. I can see wireless networks just can't connect to them

---

### Post by dch921 on 2013-01-22
Found the issue was with the number of DHCP clients on the router. It had been changed sometime yesterday to only 5 when upping it to 20 was able to connect without issue.

---

