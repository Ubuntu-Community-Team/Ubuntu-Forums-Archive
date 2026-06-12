---
title: "Slow and intermittent wireless - Ubuntu 12.04.01 LTS on Asus X58L"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by Peter_W on 2013-01-20
Hi, I have been experiencing wireless issues. Everything had been working fine up until about 2 weeks ago, when the Internet connection through my laptop became slow and unreliable. None of the other devices that connect to the wireless have had problems and the signal strength is good. It sometimes takes a few minutes to connect at start up but usually succeeds eventually, but then often loses the Internet connection after some time, from a few seconds to hours after it connects - sometimes it manages to remain connected for a whole session. The wireless connection indicator usually says the connection is alive when the Internet connection goes down - sometimes the wireless connection does disconnect itself as well. The Internet connection sometimes automatically reconnects after a few minutes but usually it seems not to. Disabling then re-enabling the wireless connection sometimes causes it to resume the Internet connection, and sometimes it does not. This has been puzzling me a lot!

The behaviour does not seem to occur in response to any particular behaviour - I'm usually just browsing in Firefox 18.0.

The wireless hardware is Atheros AR928X. The kernel architecture is 3.2.0-29-generic i686 as given by 'uname -mr'.

More output following the suggestions at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) is below, thanks for any suggestions you can give.

ifconfig output:

```
wlan0     Link encap:Ethernet  HWaddr 00:22:43:23:8f:cd  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe23:8fcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28708500 (28.7 MB)  TX bytes:7980726 (7.9 MB)

```

iwconfig output:

```
wlan0     IEEE 802.11bgn  ESSID: wisc169br  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:C6:B1:65   
          Bit Rate=13 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1351  Invalid misc:92   Missed beacon:0

```

'lsmod' output does not seem to contain any information referring to the wireless.

Output of 'dmesg | grep "wlan"':

```
[   41.657335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.660994] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.630810] wlan0: authenticate with 68:7f:74:c6:b1:65 (try 1)
[   44.632811] wlan0: authenticated
[   44.652058] wlan0: associate with 68:7f:74:c6:b1:65 (try 1)
[   44.655609] wlan0: RX AssocResp from 68:7f:74:c6:b1:65 (capab=0x411 status=0 aid=5)
[   44.655614] wlan0: associated
[   44.662872] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.912064] wlan0: no IPv6 routers present

```

Output of 'sudo lshw -C network':

```
*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:43:23:8f:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.117 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fdef0000-fdefffff

```

Output of 'iwlist scan':

```
wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:C6:B1:65
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"wisc169br"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010489152192
                    Extra: Last beacon: 19732ms ago
                    IE: Unknown: 0009776973633136396272
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD840050F204104A00011010440001021041000100103B000103104700100B741A28F7D61530ABE7F124A9B9B2C010210005436973636F1023000B436973636F2058323030301024000558323030301042000E30313331304A30343132303535311054000800060050F20400011011000A436973636F3230353531100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

