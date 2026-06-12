---
title: "Intel Centrino Wireless N 1000 wireless card not working properly?"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by bloodworth on 2012-07-24
Hey, I'm having trouble connecting to my router, which is weird because I could do it momentarily before it refused to connect. 
I can see wifi's and try to connect but it will not complete the action. 
I've included some info that may be of use for you, but notify me if any info is missing.
```


mahler@mahler-N53Jq:~$ sudo lshw -class network
[sudo] password for mahler: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:50:11:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-27-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:54 memory:d6e00000-d6e01fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:9a:55:f1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:56 memory:d3200000-d323ffff ioport:8000(size=128)

mahler@mahler-N53Jq:~$ dmesg | grep iwl
[   16.063622] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.063630] iwlwifi 0000:03:00.0: setting latency timer to 64
[   16.063653] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   16.063655] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[   16.063658] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   16.063733] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[   16.063762] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   16.063826] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.082415] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   16.082417] iwlwifi 0000:03:00.0: Device SKU: 0X50
[   16.082418] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   16.082431] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   16.134673] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   16.493088] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

mahler@mahler-N53Jq:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Thank you / bw

---

### Post by chili555 on 2012-07-24
What does this tell us?```
dmesg | grep wlan
rfkill list all
iwconfig
```Thanks.

---

### Post by bloodworth on 2012-07-24
```

[   17.141427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  747.337296] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  749.753983] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  749.953711] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  750.153849] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  750.353733] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  758.044593] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  758.242496] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  758.442485] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  758.642503] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  766.335463] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  766.535085] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  766.735186] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  766.935204] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  774.626417] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  774.823675] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  775.023740] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  775.223739] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  782.919544] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  783.116616] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  783.316231] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  783.516328] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  791.320999] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  791.521148] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  791.721101] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  791.921038] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  799.707752] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  799.905734] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  800.105794] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  800.305695] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  807.995745] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  808.194397] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  808.394330] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  808.594430] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  816.285754] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  816.483072] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  816.687042] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  816.883110] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  824.568871] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  824.767735] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  824.967728] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  825.171687] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[  832.867582] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[  833.064195] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[  833.264327] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[  833.464375] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10468.522138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10470.850408] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10471.047460] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10471.247389] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10471.447364] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10479.140430] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10479.344090] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10479.543986] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10479.743893] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10487.498746] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10487.696660] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10487.896454] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10488.096272] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10495.824666] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10496.021173] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10496.225059] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10496.424916] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10504.115982] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10504.313571] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10504.513411] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10504.713381] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10512.449261] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10512.646024] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10512.846002] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10513.045984] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10518.752283] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10518.951294] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10519.151149] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10519.351134] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10527.043418] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10527.239910] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10527.439741] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10527.639617] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10535.334712] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10535.536426] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10535.736318] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10535.940281] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10543.625494] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10543.824806] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10544.024854] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10544.228787] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10551.912976] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10552.109508] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10552.309337] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10552.509330] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10560.207591] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10560.405806] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10560.605871] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10560.805832] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10568.497192] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10568.694352] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10568.894208] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10569.094144] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10576.788261] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10576.986833] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10577.186858] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10577.386726] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10585.080068] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10585.279452] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10585.479276] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10585.679074] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10596.852127] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10597.050477] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10597.250336] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10597.450299] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10605.243704] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10605.442775] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10605.642707] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10605.842633] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10611.590074] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10611.788179] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10611.988135] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10612.187887] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10619.837286] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10620.036748] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10620.236741] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10620.436593] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10628.164018] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10628.361212] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10628.561159] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10628.761091] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10634.515439] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10634.714615] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10634.914574] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10635.114421] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10642.809375] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10643.007145] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10643.207060] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10643.406855] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10651.099933] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10651.299465] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10651.499437] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10651.699351] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10956.625322] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10956.822402] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10957.022333] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10957.222228] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10964.930921] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10965.131024] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10965.334962] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10965.534837] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10973.206509] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10973.403420] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10973.603328] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10973.803353] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10981.511851] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10981.707938] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10981.907830] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10982.107752] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10989.796746] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10989.996457] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10990.196330] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10990.396256] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[10998.087742] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[10998.284932] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[10998.484892] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[10998.684749] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11006.378885] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11006.577418] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11006.777390] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11006.981398] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11014.669386] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11014.865912] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11015.065898] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11015.268834] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11022.960535] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11023.158532] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11023.358318] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11023.558303] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11031.258585] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11031.454946] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11031.654938] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11031.858891] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11039.542555] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11039.739424] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11039.939357] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11040.139273] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11047.833112] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11048.031994] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11048.231962] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11048.431746] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11056.219518] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11056.416426] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11056.616399] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11056.816211] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11064.517082] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11064.716903] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11064.916802] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11065.116736] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11072.847532] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11073.045448] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11073.245392] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11073.445332] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11082.634591] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11082.833297] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11083.033267] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11083.233147] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11090.927780] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11091.125775] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11091.325660] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11091.525544] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11099.214956] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11099.414361] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11099.614280] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11099.818065] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11107.509531] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11107.706727] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11107.906767] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11108.106546] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11115.803727] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11116.003253] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11116.203183] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11116.403082] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11124.088292] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11124.287837] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11124.487715] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11124.691635] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11132.372036] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11132.568239] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11132.768243] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11132.968437] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11140.672861] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11140.876761] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11141.076714] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11141.276537] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11148.955017] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11149.153242] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11149.353171] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11149.553067] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11157.251690] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11157.450028] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11157.649783] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11157.849564] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11165.542916] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11165.742309] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11165.942124] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11166.142044] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11173.842204] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11174.038742] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11174.238653] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11174.438560] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11182.124197] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11182.323271] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11182.523229] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11182.723065] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11190.408820] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11190.607879] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11190.807688] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11191.007606] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11198.708609] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11198.908247] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11199.108178] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11199.308072] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11505.471027] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11505.670758] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11505.870719] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11506.070587] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11513.760269] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11513.959352] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11514.159231] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11514.359091] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11522.096590] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11522.295774] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11522.497194] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11522.695585] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11530.433531] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11530.632219] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11530.832138] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11531.032143] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11538.759144] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11538.956784] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11539.156605] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11539.356506] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11547.026035] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11547.225344] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11547.429214] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11547.629109] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11555.411697] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11555.609727] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11555.809603] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11556.009592] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11563.813316] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11564.010169] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11564.210038] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11564.409986] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11572.205572] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11572.402707] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11572.602503] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11572.802493] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11580.598802] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11580.795116] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11580.995040] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11581.194926] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11588.889682] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11589.087629] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11589.287534] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11589.487444] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11597.180529] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11597.380105] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11597.579950] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11597.779866] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11605.472319] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11605.668628] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11605.868450] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11606.068484] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11614.683914] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11614.880713] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11615.080607] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11615.280524] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11623.036367] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11623.233129] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11623.433032] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11623.633015] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11631.419817] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11631.617653] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11631.817529] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11632.017412] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11639.663149] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11639.862158] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11640.062017] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11640.262012] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11647.948969] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11648.146614] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11648.346507] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11648.546433] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11656.239787] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11656.439104] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11656.639114] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11656.838957] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11664.531152] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11664.727653] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11664.927588] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11665.127521] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11672.821582] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11673.024148] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11673.224013] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11673.424015] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11681.112564] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11681.308893] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11681.508652] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11681.708504] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11689.403262] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11689.601147] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11689.801037] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11690.000955] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11697.624496] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11697.821632] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11698.021586] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11698.225487] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11705.882471] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11706.082179] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11706.282076] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11706.482048] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11714.173544] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11714.370791] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11714.570679] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11714.770475] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11722.464127] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11722.663307] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11722.863185] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11723.063165] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11730.755199] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11730.951687] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11731.151606] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11731.351469] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11739.046413] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11739.244280] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11739.444163] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11739.643990] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11747.337015] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11747.536644] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11747.736646] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11747.936571] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[11996.983965] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[11997.183264] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[11997.383285] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[11997.583180] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12005.274664] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12005.471790] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12005.671712] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12005.875610] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12013.547823] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12013.744329] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12013.944222] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12014.148120] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12021.855580] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12022.052903] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12022.256861] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12022.456802] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12030.250158] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12030.449374] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12030.649211] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12030.849294] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12038.644065] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12038.841886] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12039.041665] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12039.241536] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12046.934382] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12047.134369] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12047.334249] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12047.538208] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12055.224989] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12055.422905] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12055.622873] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12055.822657] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12063.516691] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12063.715434] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12063.915355] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12064.115258] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12071.858505] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12072.055769] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12072.259724] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12072.459638] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12080.200809] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12080.400341] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12080.600334] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12080.800119] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12082.743397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12085.111987] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12085.310347] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12085.510147] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12085.710163] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12093.402707] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12093.602780] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12093.802691] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12094.002561] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12101.693948] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12101.891228] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12102.091160] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12102.291043] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12109.984594] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12110.187716] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12110.387592] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12110.591470] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12118.259134] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12118.456260] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12118.656238] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12118.856110] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12126.567597] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12126.764639] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12126.964690] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12127.164491] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12132.803997] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12133.002080] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12133.202118] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12133.401878] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12141.101734] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12141.298682] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12141.498440] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12141.698472] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12149.391575] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12149.591036] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12149.791044] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12149.990824] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12157.682584] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12157.883518] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12158.083493] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12158.283433] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12165.973752] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12166.172105] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12166.371999] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12166.575832] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12174.265663] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12174.468519] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12174.664650] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12174.864637] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12182.555208] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12182.753055] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12182.953001] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12183.152917] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12190.948559] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12191.145483] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12191.345346] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12191.545258] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12199.239330] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12199.438141] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12199.638065] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12199.837948] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12211.112404] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12211.309133] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12211.508945] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12211.708861] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12219.404921] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12219.601649] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12219.801488] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12220.001347] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12227.696360] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12227.894080] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12228.093880] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12228.293790] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12235.952267] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12236.150579] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12236.350512] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12236.550425] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12244.276970] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12244.474983] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12244.674938] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12244.874874] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12252.545687] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12252.743560] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12252.943499] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12253.143322] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12260.863110] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12261.060165] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12261.259959] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12261.459902] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12269.236545] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12269.436628] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12269.636458] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12269.836271] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12571.009253] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12571.209260] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12571.409151] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12571.612868] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12579.391269] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12579.589739] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12579.789562] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12579.989411] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12587.684340] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12587.882051] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12588.081984] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12588.281945] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12595.975330] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12596.174641] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12596.374493] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12596.574367] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12604.366709] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12604.563099] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12604.762958] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12604.963003] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12612.749628] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12612.947626] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12613.147512] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12613.347497] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12621.051573] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12621.248027] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12621.451979] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12621.651858] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12629.341840] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12629.540467] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12629.740390] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12629.940264] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12637.627543] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12637.825003] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12638.024938] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12638.224752] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12645.922004] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12646.121543] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12646.321398] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12646.521255] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12654.272036] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12654.470074] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12654.669890] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12654.869837] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12662.607237] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12662.806598] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12663.006458] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12663.206483] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12670.898402] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12671.094935] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12671.294978] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12671.494767] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12679.189282] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12679.387440] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12679.587274] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12679.787240] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12687.582252] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12687.783873] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12687.983721] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12688.183763] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12696.896322] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12697.095994] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12697.295784] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12697.495762] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12705.299646] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12705.500405] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12705.700327] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12705.900371] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12713.579678] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12713.777005] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12713.976958] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12714.180858] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12721.973719] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12722.173474] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12722.377380] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12722.577308] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12730.266829] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12730.465934] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12730.665825] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12730.865740] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12738.556982] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12738.754305] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12738.954191] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12739.154187] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12746.839290] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12747.038893] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12747.238721] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12747.438616] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12755.137746] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12755.335545] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12755.535393] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12755.735345] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12763.428886] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12763.627932] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12763.827854] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12764.027710] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12771.719471] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12771.916586] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12772.116404] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12772.316352] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12780.011118] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12780.208977] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12780.408867] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12780.608777] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12788.300678] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12788.497429] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12788.697248] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12788.897198] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12796.592166] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12796.789794] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12796.989804] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12797.189664] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12804.985543] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12805.182386] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12805.382321] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12805.582238] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out
[12813.290652] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 1/3)
[12813.486885] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 2/3)
[12813.686850] wlan0: direct probe to 1c:bd:b9:af:f4:e0 (try 3/3)
[12813.886728] wlan0: direct probe to 1c:bd:b9:af:f4:e0 timed out

mahler@mahler-N53Jq:~/Desktop$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
mahler@mahler-N53Jq:~/Desktop$ iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


```

I'm lost here, why's the direct probe timing out?

---

### Post by chili555 on 2012-07-24
Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Now does it connect? If so, we'll write one quick file to make it persistent.

---

### Post by bloodworth on 2012-07-24
It did not connect. Did I try to disable and then re-enable the module for the wifi? It just kept trying to connect as before.

---

### Post by chili555 on 2012-07-24
> Did I try to disable and then re-enable the module for the wifi?Yes, but with a driver parameter. Let's try another one:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi swcrypto=1
```Are you quite sure there is no MAC address filtering in the router? Promise??

---

### Post by bloodworth on 2012-07-24
No luck. I used the reset button on the router just to be sure, I am now trying to connect to an open network with no MAC filtering, promise.

---

### Post by chili555 on 2012-07-24
Let's see:```
dmesg | grep iwl
```Very mysterious.

---

### Post by bloodworth on 2012-07-24
```

[   16.063622] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.063630] iwlwifi 0000:03:00.0: setting latency timer to 64
[   16.063653] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   16.063655] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[   16.063658] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   16.063733] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[   16.063762] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   16.063826] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.082415] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   16.082417] iwlwifi 0000:03:00.0: Device SKU: 0X50
[   16.082418] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   16.082431] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   16.134673] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   16.493088] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  747.170232] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  747.251507] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  752.362027] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  760.674610] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  769.015360] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  777.288061] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  785.608614] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  794.017073] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  802.341799] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  810.682384] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  818.963014] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  827.235685] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  835.536513] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  847.141601] Modules linked in: vesafb parport_pc snd_hda_codec_hdmi rfcomm ppdev bnep snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_seq_midi snd_hwdep nvidia(P) snd_pcm snd_rawmidi snd_seq_midi_event iwlwifi snd_seq snd_timer snd_seq_device mac80211 joydev snd btusb soundcore bluetooth uvcvideo videodev cfg80211 snd_page_alloc psmouse v4l2_compat_ioctl32 asus_laptop video lp i7core_edac sparse_keymap edac_core serio_raw input_polldev mac_hid parport mei(C) atl1c
[10468.414568] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10473.494665] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10481.806972] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10490.171650] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10498.504040] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10506.764389] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10521.402409] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10529.706835] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10538.019306] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10546.295773] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10554.556281] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10562.876907] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10571.149389] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10579.457701] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10587.770341] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10599.553366] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10614.243086] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10622.507756] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10637.185501] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10645.445953] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10653.758562] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10959.261501] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10967.589854] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10975.858389] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10984.166872] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[10992.435430] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11000.763941] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11009.056380] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11017.312881] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11025.625358] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11033.917974] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11042.222455] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11050.530875] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11058.871319] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11067.163907] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11075.488367] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11085.284273] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11093.592701] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11101.901232] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11110.161699] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11118.442201] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11126.758767] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11134.995223] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11143.331713] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11151.612326] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11159.924725] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11168.185182] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11176.477681] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11184.798270] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11193.094654] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11201.379337] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11508.101756] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11516.410311] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11524.738764] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11533.079231] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11541.411664] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11549.708153] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11558.096684] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11566.493113] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11574.885614] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11583.254015] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11591.522538] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11599.827143] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11608.991245] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11617.343620] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11625.692073] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11634.048565] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11642.305077] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11650.605575] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11658.894068] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11667.174577] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11675.499081] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11683.743657] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11692.044143] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11700.276703] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11708.529098] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11716.821665] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11725.110169] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11733.390690] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11741.711150] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11750.011721] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[11999.638277] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12007.950922] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12016.191523] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12024.563809] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12032.924461] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12041.288893] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12049.589396] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12057.877796] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12066.174685] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12074.538719] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12082.656437] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12087.761188] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12096.093767] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12104.318170] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12112.678668] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12120.927148] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12135.457119] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12143.753481] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12152.033987] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12160.314449] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12168.659029] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12176.923453] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12185.252102] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12193.620552] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12201.909040] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12213.771984] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12222.092447] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12230.352946] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12238.601505] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12246.942071] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12255.210484] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12263.550977] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12271.931401] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12573.708119] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12581.996654] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12590.329103] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12598.669696] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12607.057964] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12615.402481] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12623.731025] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12631.943454] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12640.236123] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12648.588566] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12656.916968] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12665.269345] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12673.529898] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12681.874436] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12690.246923] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12699.586977] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12707.971427] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12716.271936] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12724.604440] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12732.936942] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12741.209468] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12749.533905] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12757.790345] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12766.102792] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12774.339426] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12782.627834] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12790.904456] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12799.284859] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12807.653260] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[12815.909939] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13122.380465] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13130.720991] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13139.081338] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13147.354021] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13155.666489] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13163.942992] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13172.259340] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13180.523849] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13188.808393] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13197.088833] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13211.650947] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13219.959302] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13228.215865] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13236.524203] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13248.399404] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13256.699899] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13264.980338] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13273.288658] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13281.549271] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13289.865687] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13298.122256] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13306.414741] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13314.719268] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13323.039697] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13331.408240] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13339.688614] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13347.945221] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13356.285697] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13364.590225] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13671.180873] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13679.493419] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13687.833680] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13696.066355] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13704.387021] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13712.679346] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13720.975831] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13729.240252] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13737.556822] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13745.837351] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13754.157737] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13762.374448] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13770.646918] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13778.903367] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13787.191824] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13797.111731] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13805.448293] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13813.836686] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13822.093248] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13830.401548] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13838.686046] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13846.938688] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13855.299116] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13863.527604] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13871.856212] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13880.164657] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13888.461122] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13896.837551] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13905.086126] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[13913.454699] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14219.933231] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14228.281799] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14236.586215] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14244.954606] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14253.215304] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14261.551786] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14269.852259] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14278.192631] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14286.437266] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14294.765678] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14303.098164] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14311.370664] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14319.659924] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14327.891687] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14336.172153] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14351.601789] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14359.894180] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14373.884265] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14382.088830] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14390.377152] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14398.613667] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14408.913525] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14417.265928] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14425.606411] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14433.882972] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14442.195431] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14450.568035] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14458.872467] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14467.160869] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14768.705521] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14777.009973] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14785.370564] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14793.683032] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14801.991653] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14810.339918] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14818.632576] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14826.948931] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14840.955156] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14849.307609] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14857.592134] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14865.896525] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14874.148994] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14882.497510] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14890.710113] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14898.982623] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14907.239197] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14915.591699] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14924.004003] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14932.360498] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14946.362698] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14957.633825] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14965.934369] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14979.920540] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14988.192972] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[14996.517480] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15004.825852] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15013.158524] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15317.521910] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15325.822496] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15334.114890] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15342.359524] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15350.671863] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15358.980373] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15367.256974] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15375.621377] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15383.997977] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15392.342381] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15400.666877] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15408.895374] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15417.259802] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15425.652258] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15434.020777] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15443.412922] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15451.673401] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15460.025889] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15468.278221] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15482.308293] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15490.628903] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15498.797452] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15507.089976] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15515.366533] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15523.682940] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15531.967414] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15540.227927] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15548.560512] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15556.864845] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15565.125378] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15866.270266] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15874.554752] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15888.536959] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15896.801455] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15905.086031] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15913.398539] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15921.750878] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15930.059307] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15938.403924] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15946.664365] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15955.000963] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15963.333232] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15971.689809] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15979.982237] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15988.214765] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[15996.579274] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16004.803809] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16013.064454] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16021.368868] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16029.669421] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16037.985900] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16046.306263] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16055.210545] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16063.531006] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16071.875639] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16080.208727] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16088.500428] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16096.760905] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16105.001703] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16113.346015] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16415.022737] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16423.375209] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16431.703683] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16439.956084] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16448.256771] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16456.565237] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16464.945585] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16473.246059] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16481.514672] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16489.823028] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16498.143716] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16506.424157] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16514.692645] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16522.985000] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16531.237643] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16540.961483] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16549.298135] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16557.610431] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16565.894877] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16579.906625] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16588.191261] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16596.479723] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16611.241432] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16617.902993] iwlwifi 0000:03:00.0: PCI INT A disabled
[16641.510609] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[16641.510630] iwlwifi 0000:03:00.0: setting latency timer to 64
[16641.510658] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[16641.510660] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[16641.510662] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[16641.510835] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[16641.510891] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[16641.511004] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16641.544190] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[16641.544192] iwlwifi 0000:03:00.0: Device SKU: 0X50
[16641.544193] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[16641.544202] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[16641.546852] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[16641.547366] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[16641.565117] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16641.646810] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16646.730461] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16655.018863] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16663.335607] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16674.658771] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16689.336438] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16695.310151] iwlwifi 0000:03:00.0: PCI INT A disabled
[16705.467984] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[16705.468005] iwlwifi 0000:03:00.0: setting latency timer to 64
[16705.468033] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[16705.468035] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[16705.468037] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[16705.468203] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[16705.468257] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[16705.468371] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16705.501426] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[16705.501428] iwlwifi 0000:03:00.0: Device SKU: 0X50
[16705.501430] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[16705.501439] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[16705.505461] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[16705.505950] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[16705.516622] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16705.599745] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16710.671500] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16718.964086] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16727.236526] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16735.560834] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16743.893440] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16752.281909] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16760.569157] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16768.833002] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[16851.570297] iwlwifi 0000:03:00.0: PCI INT A disabled
[16903.598381] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[16903.598405] iwlwifi 0000:03:00.0: setting latency timer to 64
[16903.598447] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[16903.598452] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[16903.598457] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[16903.598634] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[16903.598700] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[16903.598822] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16903.632415] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[16903.632420] iwlwifi 0000:03:00.0: Device SKU: 0X50
[16903.632424] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[16903.632460] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[16903.635437] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[16903.635766] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[16903.653949] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16903.738146] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17070.745497] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17079.086067] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17087.366564] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17095.666981] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17103.963557] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17112.331940] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17120.612417] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17128.968967] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17137.345480] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17145.729870] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17154.002333] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17168.020362] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17176.324983] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17190.355181] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17198.647548] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17206.911970] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17215.220621] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17223.501150] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17231.793505] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17240.090104] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17248.430537] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17259.645853] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17267.922346] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17276.198823] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17284.495197] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17292.811821] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17301.092273] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17309.360905] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17317.677303] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17619.585868] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17627.930487] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17636.242885] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17644.595420] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17652.879674] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17661.264301] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17669.580904] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17677.865264] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17686.101862] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17694.410196] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17702.746727] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17711.023291] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17719.279820] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17727.636165] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17735.928767] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17745.420896] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17753.717348] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17761.981866] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17770.262357] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17778.638735] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17786.991243] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17795.299697] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17803.648176] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17811.948714] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17820.233228] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17828.493790] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17836.758240] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17845.022767] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17853.419285] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[17861.687673] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18168.266377] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18182.188389] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18190.433046] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18198.773519] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18207.070004] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18215.358426] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18223.646827] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18231.931371] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18240.215943] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18248.484516] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18256.756933] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18265.065317] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18273.381940] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18281.642579] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18289.946837] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18298.267400] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18306.528032] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18314.796552] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18323.068996] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18331.401467] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18339.710043] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18347.986397] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18362.913885] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18371.228166] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18372.479871] iwlwifi 0000:03:00.0: PCI INT A disabled
[18385.287873] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[18385.287895] iwlwifi 0000:03:00.0: setting latency timer to 64
[18385.287922] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[18385.287925] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90011084000
[18385.287927] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[18385.288088] iwlwifi 0000:03:00.0: irq 54 for MSI/MSI-X
[18385.288143] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[18385.288256] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18385.321072] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[18385.321074] iwlwifi 0000:03:00.0: Device SKU: 0X50
[18385.321075] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[18385.321149] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[18385.323913] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[18385.324315] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[18385.341929] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18385.424342] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18390.504123] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18398.792590] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18407.165031] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18415.513511] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18423.778165] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18432.066523] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18440.411215] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18448.735531] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18500.137371] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18508.397676] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18516.702293] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18525.050660] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18533.351357] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18541.687707] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18549.968310] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18776.766531] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18785.019063] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18793.295556] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18801.660018] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18810.008473] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18818.308858] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18826.572654] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18834.813291] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18843.133785] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18851.450377] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18859.746782] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18868.079227] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18876.443775] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18884.724216] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18899.218123] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18907.558619] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18915.855233] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18930.509042] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18938.789466] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18947.057906] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18955.346382] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18965.890001] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18974.162554] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18982.446916] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18990.731631] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[18999.071978] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19007.348570] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19015.628959] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19023.885510] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19325.798046] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19334.030672] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19348.720525] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19357.016907] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19365.233517] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19379.935345] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19388.863509] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19397.143978] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19405.412400] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19413.680935] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19422.005638] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19430.321974] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19438.594399] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19446.898892] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19455.271365] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19463.639921] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19478.257727] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19498.665220] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19506.933652] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19515.194141] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19529.776028] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19538.116559] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19546.477067] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19554.861541] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19563.161906] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19874.498529] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19882.803073] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19891.083607] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19899.379988] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19907.712505] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19916.021042] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19924.289414] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19932.550014] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19940.850490] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19949.118986] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19957.479593] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19965.768106] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19974.096394] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19982.472961] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[19990.789542] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20006.746677] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20015.035187] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20023.287825] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20031.620313] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20039.960594] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20054.554473] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20063.454823] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20071.755286] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20080.127658] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20088.432328] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20096.740684] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20105.069123] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20113.425638] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[20121.754123] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues

```

My guess is that something failed to flush...  8)

---

### Post by chili555 on 2012-07-24
Wonderful! You have an official bug: [https://bugzilla.redhat.com/show_bug.cgi?id=805285](https://bugzilla.redhat.com/show_bug.cgi?id=805285)

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2359](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2359)

Let's try the driver parameter mentioned:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi wd_disable=1
```You might also install linux-backports-modules-cw-3.3-precise-generic or -pae to match your running kernel:```
uname -r
```

---

### Post by bloodworth on 2012-07-24
Neither of the parameters for the modprobe iwlwifi seem to work, I've tried both the wd_disable=1 and 11n_disable=1.

I misinterpreted the use of the uname -r command at first. I've sudo apt-get both the packages, but it continues to disconnect after a period of trying to connect.

---

### Post by bloodworth on 2012-07-24
Ok, I am on the brink of panic here. I tried a reboot after installing the modules but it wouldn't start as usual. Something about a missing /init seemed to be the problem. Booted up the grub and loaded an old version of ubuntu and here I am. What should I do?

ps. Wireless still not working.

---

