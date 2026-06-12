---
title: "wireless still not working on Thinkpad T61 w/  Intel 4965 AG"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by cincinnatus on 2008-12-20
Thinkpad T61
Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection
Ubuntu 8.04.1

I posted [awhile ago]("http://ubuntuforums.org/showthread.php?t=974344") that my wireless didn't work, and eventually concluded that the problem was with my router, because the Windows PCs on my network were having finicky wireless connections as well, and I could connect to the wireless at the local library without any problems.

But today we changed the channel on the router because we figured the problem was too much interference from a nearby network.

Now the wireless on the Windows PCs works fine.

I have a dual boot Windows XP/Ubuntu, and when I boot into Windows, the wireless works just as well as on the other Windows PCs on our network.

I adjusted the Wireless properties in Network Settings, and the Network Manager thingie on the panel says I am connected to the wireless network. However, I can't get on any websites. I can't ping them either.

```

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:52:5f:0f  
          inet6 addr: fe80::21f:3bff:fe52:5f0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16443 (16.0 KB)  TX bytes:13255 (12.9 KB)
```

```

$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Moberly"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1E:2A:DE:0A:B3   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-36 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:d4:12:be
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:52:5f:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
```

```

$ dmesg | grep -i wlan0
[ 1642.063298] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063305] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063312] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063319] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063325] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063332] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063338] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063345] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063351] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1642.063358] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 1642.063900] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 1646.378194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1646.512163] wlan0: Initial auth_alg=0
[ 1646.512168] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 1646.513901] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 1646.513904] wlan0: authenticated
[ 1646.513906] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 1646.516872] wlan0: RX AssocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=2)
[ 1646.516876] wlan0: associated
[ 1646.516905] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 1646.516908] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1646.516910] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1646.516912] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1646.518294] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1657.156203] wlan0: no IPv6 routers present
[ 1865.228276] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1866.823390] wlan0: Initial auth_alg=0
[ 1866.823402] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 1866.825131] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 1866.825139] wlan0: authenticated
[ 1866.825144] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 1866.828256] wlan0: RX AssocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=2)
[ 1866.828264] wlan0: associated
[ 1866.828330] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 1866.828337] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1866.828343] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1866.828348] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1866.832214] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1877.657862] wlan0: no IPv6 routers present
[ 1946.029250] wlan0: RX WEP frame, decrypt failed
[ 1946.259839] wlan0: RX WEP frame, decrypt failed
[ 1947.259561] wlan0: RX WEP frame, decrypt failed
[ 1950.999565] wlan0: RX WEP frame, decrypt failed
[ 1951.000675] wlan0: RX WEP frame, decrypt failed
[ 1951.060665] wlan0: RX WEP frame, decrypt failed
[ 1951.132842] wlan0: RX WEP frame, decrypt failed
[ 1951.138640] wlan0: RX WEP frame, decrypt failed
[ 1951.200556] wlan0: RX WEP frame, decrypt failed
[ 1951.272498] wlan0: RX WEP frame, decrypt failed
[ 1951.274221] wlan0: RX WEP frame, decrypt failed
[ 1951.334167] wlan0: RX WEP frame, decrypt failed
[ 1951.419201] wlan0: RX WEP frame, decrypt failed
[ 1951.442543] wlan0: RX WEP frame, decrypt failed
[ 1951.670864] wlan0: RX WEP frame, decrypt failed
[ 1951.922731] wlan0: RX WEP frame, decrypt failed
[ 1952.121017] wlan0: RX WEP frame, decrypt failed
[ 1952.279305] wlan0: RX WEP frame, decrypt failed
[ 1952.380002] wlan0: RX WEP frame, decrypt failed
[ 1952.489070] wlan0: RX WEP frame, decrypt failed
[ 1952.717523] wlan0: RX WEP frame, decrypt failed
[ 1952.969012] wlan0: RX WEP frame, decrypt failed
[ 1953.168370] wlan0: RX WEP frame, decrypt failed
[ 1953.290337] wlan0: RX WEP frame, decrypt failed
[ 1953.310888] wlan0: RX WEP frame, decrypt failed
[ 1953.378244] wlan0: RX WEP frame, decrypt failed
[ 1953.609440] wlan0: RX WEP frame, decrypt failed
[ 1953.622347] wlan0: RX WEP frame, decrypt failed
[ 1953.865428] wlan0: RX WEP frame, decrypt failed
[ 1954.347897] wlan0: RX WEP frame, decrypt failed
[ 1954.863798] wlan0: RX WEP frame, decrypt failed
[ 1955.053692] wlan0: RX WEP frame, decrypt failed
[ 1955.055119] wlan0: RX WEP frame, decrypt failed
[ 1955.305440] wlan0: RX WEP frame, decrypt failed
[ 1955.376262] wlan0: RX WEP frame, decrypt failed
[ 1955.556902] wlan0: RX WEP frame, decrypt failed
[ 1955.558190] wlan0: RX WEP frame, decrypt failed
[ 1955.756683] wlan0: RX WEP frame, decrypt failed
[ 1956.434797] wlan0: RX WEP frame, decrypt failed
[ 1956.889001] wlan0: RX WEP frame, decrypt failed
[ 1957.767986] wlan0: RX WEP frame, decrypt failed
[ 1958.856415] wlan0: RX WEP frame, decrypt failed
[ 1959.022406] wlan0: RX WEP frame, decrypt failed
[ 1959.372803] wlan0: RX WEP frame, decrypt failed
[ 1962.848900] wlan0: RX WEP frame, decrypt failed
[ 1967.356527] wlan0: RX WEP frame, decrypt failed
[ 1974.224039] wlan0: RX WEP frame, decrypt failed
[ 1974.226595] wlan0: RX WEP frame, decrypt failed
[ 1983.336126] wlan0: RX WEP frame, decrypt failed
[ 2015.288815] wlan0: RX WEP frame, decrypt failed
[ 2079.203780] wlan0: RX WEP frame, decrypt failed
[ 2207.029025] wlan0: RX WEP frame, decrypt failed
[ 2302.968153] wlan0: RX WEP frame, decrypt failed
[ 2303.062349] wlan0: RX WEP frame, decrypt failed
[ 2348.441424] wlan0: RX WEP frame, decrypt failed
[ 2348.444850] wlan0: RX WEP frame, decrypt failed
[ 2349.166434] wlan0: RX WEP frame, decrypt failed
[ 2349.167621] wlan0: RX WEP frame, decrypt failed
[ 2349.915477] wlan0: RX WEP frame, decrypt failed
[ 2349.916532] wlan0: RX WEP frame, decrypt failed
[ 2350.664380] wlan0: RX WEP frame, decrypt failed
[ 2350.668253] wlan0: RX WEP frame, decrypt failed
[ 2425.597619] wlan0: RX WEP frame, decrypt failed
[ 2425.600017] wlan0: RX WEP frame, decrypt failed
[ 2462.675442] wlan0: RX WEP frame, decrypt failed
[ 2692.836506] wlan0: RX WEP frame, decrypt failed
[ 2692.839165] wlan0: RX WEP frame, decrypt failed
[ 2973.963865] wlan0: RX WEP frame, decrypt failed
[ 3108.116892] wlan0: RX WEP frame, decrypt failed
[ 3108.210323] wlan0: RX WEP frame, decrypt failed
[ 3108.222855] wlan0: RX WEP frame, decrypt failed
[ 3108.226330] wlan0: RX WEP frame, decrypt failed
[ 3108.230009] wlan0: RX WEP frame, decrypt failed
[ 3108.233858] wlan0: RX WEP frame, decrypt failed
[ 3108.237312] wlan0: RX WEP frame, decrypt failed
[ 3108.241028] wlan0: RX WEP frame, decrypt failed
[ 3108.244709] wlan0: RX WEP frame, decrypt failed
[ 3108.249684] wlan0: RX WEP frame, decrypt failed
[ 3108.253220] wlan0: RX WEP frame, decrypt failed
[ 3108.256819] wlan0: RX WEP frame, decrypt failed
[ 3108.260461] wlan0: RX WEP frame, decrypt failed
[ 3108.264091] wlan0: RX WEP frame, decrypt failed
[ 3108.267831] wlan0: RX WEP frame, decrypt failed
[ 3108.271237] wlan0: RX WEP frame, decrypt failed
[ 3266.450857] wlan0: RX WEP frame, decrypt failed
[ 3266.453088] wlan0: RX WEP frame, decrypt failed
[ 3269.031214] wlan0: RX WEP frame, decrypt failed
[ 3269.034837] wlan0: RX WEP frame, decrypt failed
[ 3271.267770] wlan0: RX WEP frame, decrypt failed
[ 3271.270222] wlan0: RX WEP frame, decrypt failed
[ 3271.283940] wlan0: RX WEP frame, decrypt failed
[ 3271.287283] wlan0: RX WEP frame, decrypt failed
[ 3324.435999] wlan0: RX WEP frame, decrypt failed
[ 3324.440342] wlan0: RX WEP frame, decrypt failed
[ 3410.088783] wlan0: RX WEP frame, decrypt failed
[ 3410.091401] wlan0: RX WEP frame, decrypt failed
[ 3632.792821] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3632.866196] wlan0: Initial auth_alg=0
[ 3632.866206] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3632.867946] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3632.867953] wlan0: authenticated
[ 3632.867957] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3632.872047] wlan0: RX AssocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=2)
[ 3632.872054] wlan0: associated
[ 3632.872113] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 3632.872119] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 3632.872126] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 3632.872131] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 3632.931324] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3632.933476] wlan0: Initial auth_alg=0
[ 3632.933487] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3632.935198] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3632.935202] wlan0: authenticated
[ 3632.935203] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3632.940127] wlan0: RX ReassocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=2)
[ 3632.940131] wlan0: associated
[ 3632.940160] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 3632.940162] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 3632.940165] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 3632.940167] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 3643.403892] wlan0: no IPv6 routers present
[ 3787.674175] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3789.235882] wlan0: Initial auth_alg=0
[ 3789.235893] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3789.235912] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3789.237610] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3789.237619] wlan0: authenticated
[ 3789.237623] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3789.237629] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 3789.431753] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3819.466958] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3835.439922] wlan0: Initial auth_alg=0
[ 3835.439933] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3835.443544] wlan0: Initial auth_alg=0
[ 3835.443551] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3835.443570] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3835.443575] wlan0: authenticated
[ 3835.443579] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3835.447355] wlan0: Initial auth_alg=0
[ 3835.447363] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3835.447381] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3835.447385] wlan0: authenticated
[ 3835.447389] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3835.451549] wlan0: authentication frame received from 00:1e:2a:de:0a:b3, but not in authenticate state - ignored
[ 3835.452786] wlan0: RX AssocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=1)
[ 3835.452793] wlan0: associated
[ 3835.452858] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 3835.456684] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3835.462419] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 3835.463022] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 3835.464007] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 3845.474025] wlan0: no IPv6 routers present
[ 3880.065021] wlan0: deauthenticate(reason=3)
[ 3881.397059] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3883.394279] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3886.265396] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265407] wlan0: deauthenticated
[ 3886.265415] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265422] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265429] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265436] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265444] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265450] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265457] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265463] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265470] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265476] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265482] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265489] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.265496] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 3886.265522] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3886.266147] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3886.268895] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 3886.268901] wlan0: authenticated
[ 3886.268906] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 3886.268913] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[ 3887.263937] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3893.219309] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219318] wlan0: deauthenticated
[ 3893.219326] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219333] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219339] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219346] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219352] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219359] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219365] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219372] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219378] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219384] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219390] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219396] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219402] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3893.219427] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3893.219851] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978675] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978689] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978697] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978704] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978711] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978717] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978723] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978730] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978737] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978743] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978751] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978758] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978764] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978771] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3922.978778] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3922.979037] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147057] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147070] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147078] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147085] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147091] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147098] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147104] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147112] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147118] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147125] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147132] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147139] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147146] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147152] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147159] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147165] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3953.147172] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3953.147437] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110226] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110240] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110248] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110256] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110262] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110269] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110276] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110282] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110290] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110296] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110303] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110309] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110315] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110321] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 3983.110328] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 3983.110802] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073939] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073952] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073959] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073966] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073973] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073979] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073986] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.073992] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074010] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074016] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074023] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074030] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074036] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074043] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074049] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4013.074057] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4013.074638] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745813] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745833] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745840] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745847] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745853] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745860] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745866] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745872] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745878] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745885] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745891] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745897] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745903] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4142.745910] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4142.746647] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436325] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436338] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436345] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436352] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436359] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436366] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436373] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436379] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436386] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436393] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436399] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436406] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436412] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4178.436419] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4178.436709] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990679] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990694] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990701] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990708] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990715] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990723] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990729] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990736] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990743] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990750] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990756] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990764] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990770] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990776] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990783] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4207.990790] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4207.991330] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954486] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954492] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954494] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954497] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954500] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954503] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954505] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954508] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954511] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954514] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954516] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954519] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954522] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954525] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954528] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4237.954531] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4237.955973] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815894] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815911] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815919] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815926] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815932] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815939] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815946] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815983] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815990] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.815996] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.816003] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.816009] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.816016] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.816022] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4267.816031] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4267.819147] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983785] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983799] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983806] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983813] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983819] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983825] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983832] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983839] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983846] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983852] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983859] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983866] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983872] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983879] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4297.983886] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4297.984283] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742626] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742640] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742647] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742654] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742660] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742667] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742675] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742681] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742687] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742694] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742700] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742706] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742712] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4327.742719] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4327.743652] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824369] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824383] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824390] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824398] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824404] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824412] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824418] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824426] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824433] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824440] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824447] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824454] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824461] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824468] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824475] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4457.824483] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4457.824835] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763613] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763629] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763637] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763643] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763650] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763657] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763664] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763670] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763677] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763684] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763691] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763697] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763704] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763710] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763717] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4504.763724] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[ 4504.764959] wlan0: RX deauthentication from 00:1e:2a:de:0a:b3 (reason=6)
[ 4528.598220] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4528.604132] wlan0: Initial auth_alg=0
[ 4528.604136] wlan0: authenticate with AP 00:1e:2a:de:0a:b3
[ 4528.605854] wlan0: RX authentication from 00:1e:2a:de:0a:b3 (alg=0 transaction=2 status=0)
[ 4528.605857] wlan0: authenticated
[ 4528.605859] wlan0: associate with AP 00:1e:2a:de:0a:b3
[ 4528.609331] wlan0: RX AssocResp from 00:1e:2a:de:0a:b3 (capab=0x431 status=0 aid=1)
[ 4528.609333] wlan0: associated
[ 4528.609363] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 4528.609365] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 4528.609368] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 4528.609370] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 4528.610675] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4538.754707] wlan0: no IPv6 routers present

```

Can somebody help me figure out what the problem is?

---

### Post by xjcannonx on 2008-12-20
I believe your problem is hardy, well from what iv'e looked at your card is really hard to get working in 8.04 but a simple upgrade to 8.10 will fix the problem.

Is this an option for you?

---

### Post by cincinnatus on 2008-12-20
Yes, I'm considering it.
But I have NVidia and I'm wondering if it will have problems...

---

### Post by xjcannonx on 2008-12-20
Yeah i don't think that should be a problem, I am doing great with my nvidia card after using the restricted drivers version 177 I think, but nvidia has an update to that on their website (version 180.xx i think) and people on the forums say that version works really good.

---

### Post by cincinnatus on 2008-12-20
Well, that sounds like a good idea then.

---

### Post by cincinnatus on 2009-01-06
This is really lame. I installed Intrepid, and I still have the same problem I had in Hardy when I first installed it: I can view my wireless network, but I can't connect to it. It's there, but forever out of reach.

Help!

---

### Post by cincinnatus on 2009-01-07
Woah! All of the sudden, I logged in to Ubuntu, and the wireless connected right off! I don't know why it's working, but let's hope it keeps working.

I have a suspicion that the problem might have been interference from other networks nearby, but I thought I fixed that problem by changing the frequency of my router. Well, maybe it's fixed now.

---

### Post by cincinnatus on 2009-01-07
Nope, still not working.

I restarted my computer and the wireless wasn't working again. I guess that was just a random one-time thing. It's the first time I've ever been able to connect to my network, though.

Network Manager tries to connect over and over again, and keeps asking me for the WEP key, which I already typed into the box. Eventually I just get tired of it and press cancel, because my wired connection works fine.

---

### Post by jdelasalas on 2009-01-07
This happened to me, its because the drivers or something don't load in the right order

sudo rmmod ndiswrapper; sudo rmmod b43; sudo rmmod ssb

then 

sudo modprobe ndiswrapper; sudo modprobe ssb

I do that everytime I log in.  I'm not sure how to automate it.

---

### Post by Favux on 2009-01-07
Hi cincinnatus,

A bunch of us have had similar problems and solved it by using gconf editor as shown here:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Hope this helps.

---

