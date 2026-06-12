---
title: "wlan won't work in ubuntustudio 9.10 but works in ubuntu 9.10??"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by 5MilesOut on 2010-01-16
Hi, my network was a dream to set up under ubuntu 9.10.  all i had to do was enter pass key, then that was it.  Works brilliantly.

Different matter with studio.  The thing I notice in network connections is, it doesn't want to retain my pass phrase, if I go back into properties the phrase is blank.  As far as I can tell the wireless card has been reconcognized and is communicating with router.

My system is:  asus p5ql-vm epu, intel core2 duo 2.8 e7400, 4gb 1067 ddr2 ram, belkin f5d7050 v4000, edimax router.

Here is the info requested in the sticky: 

kevin@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 008 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


kevin@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:51:70:42  
          inet6 addr: fe80::217:3fff:fe51:7042/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4746 (4.7 KB)  TX bytes:12923 (12.9 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:17:3f:51:70:42  
          inet addr:169.254.5.147  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-51-70-42-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


kevin@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:1F:35:6D:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=48/100  
                    Encryption key:on
                    ESSID:"Default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fd699bf16
                    Extra: Last beacon: 957ms ago
                    IE: Unknown: 000744656661756C74
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4301000000
          Cell 02 - Address: 00:24:17:C5:2A:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=9/100  Signal level=9/100  
                    Encryption key:on
                    ESSID:"BTHomeHub2-G68N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000783f9b2e5e
                    Extra: Last beacon: 1378ms ago
                    IE: Unknown: 000F4254486F6D65487562322D4736384E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080000000000000000000000000000000000000000


kevin@ubuntu:~$ ismod | grep "wlan_module_name"
No command 'ismod' found, did you mean:
 Command 'insmod' from package 'module-init-tools' (main)
 Command 'lsmod' from package 'module-init-tools' (main)
ismod: command not found
kevin@ubuntu:~$ ismod | grep wlan_module_name
No command 'ismod' found, did you mean:
 Command 'insmod' from package 'module-init-tools' (main)
 Command 'lsmod' from package 'module-init-tools' (main)
ismod: command not found
kevin@ubuntu:~$ ismod | grep wlan_module_Default
No command 'ismod' found, did you mean:
 Command 'insmod' from package 'module-init-tools' (main)
 Command 'lsmod' from package 'module-init-tools' (main)
ismod: command not found

[    8.672281] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   10.423209] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   10.424708] wlan0: authenticated
[   10.424711] wlan0: associate with AP 00:1f:1f:35:6d:60
[   10.428205] wlan0: RX AssocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   10.428208] wlan0: associated
[   10.428772] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.879382] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   11.879388] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   11.879393] Info fld=0x12d
[   11.879395] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   11.879403] end_request: I/O error, dev sr0, sector 1200
[   12.465362] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   12.465366] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   12.465370] Info fld=0x12d
[   12.465371] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   12.465375] end_request: I/O error, dev sr0, sector 1200
[   12.465437] __ratelimit: 1 callbacks suppressed
[   12.465439] Buffer I/O error on device sr0, logical block 150
[   12.993541] CPU0 attaching NULL sched-domain.
[   12.993547] CPU1 attaching NULL sched-domain.
[   13.034193] CPU0 attaching sched-domain:
[   13.034197]  domain 0: span 0-1 level MC
[   13.034205]   groups: 0 1
[   13.034208]   domain 1: span 0-1 level CPU
[   13.034210]    groups: 0-1 (__cpu_power = 2048)
[   13.034213] CPU1 attaching sched-domain:
[   13.034214]  domain 0: span 0-1 level MC
[   13.034216]   groups: 1 0
[   13.034218]   domain 1: span 0-1 level CPU
[   13.034220]    groups: 0-1 (__cpu_power = 2048)
[   13.051645] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   13.051651] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   13.051656] Info fld=0x12d
[   13.051659] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   13.051665] end_request: I/O error, dev sr0, sector 1200
[   13.051735] Buffer I/O error on device sr0, logical block 150
[   13.638030] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   13.638034] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   13.638037] Info fld=0x12d
[   13.638039] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   13.638043] end_request: I/O error, dev sr0, sector 1200
[   13.638097] Buffer I/O error on device sr0, logical block 150
[   14.224046] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.224052] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   14.224058] Info fld=0x12d
[   14.224060] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   14.224067] end_request: I/O error, dev sr0, sector 1200
[   14.224072] Buffer I/O error on device sr0, logical block 150
[   14.810291] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   14.810296] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   14.810299] Info fld=0x12d
[   14.810300] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   14.810305] end_request: I/O error, dev sr0, sector 1200
[   14.810309] Buffer I/O error on device sr0, logical block 150
[   15.396452] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.396458] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   15.396464] Info fld=0x12d
[   15.396466] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   15.396472] end_request: I/O error, dev sr0, sector 1200
[   15.396478] Buffer I/O error on device sr0, logical block 150
[   16.243173] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.243180] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   16.243185] Info fld=0x12d
[   16.243187] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   16.243198] end_request: I/O error, dev sr0, sector 1200
[   16.243201] Buffer I/O error on device sr0, logical block 150
[   16.829442] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.829448] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   16.829453] Info fld=0x12d
[   16.829455] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   16.829462] end_request: I/O error, dev sr0, sector 1200
[   16.829467] Buffer I/O error on device sr0, logical block 150
[   17.127386] CPU0 attaching NULL sched-domain.
[   17.127390] CPU1 attaching NULL sched-domain.
[   17.171061] CPU0 attaching sched-domain:
[   17.171065]  domain 0: span 0-1 level MC
[   17.171067]   groups: 0 1
[   17.171071] CPU1 attaching sched-domain:
[   17.171072]  domain 0: span 0-1 level MC
[   17.171074]   groups: 1 0
[   18.742898] wlan0: deauthenticated (Reason: 1)
[   19.744014] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   19.746163] wlan0 direct probe responded
[   19.746165] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   19.747898] wlan0: authenticated
[   19.747901] wlan0: associate with AP 00:1f:1f:35:6d:60
[   19.750147] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   19.750149] wlan0: associated
[   21.312007] wlan0: no IPv6 routers present
[   28.060215] wlan0: deauthenticated (Reason: 1)
[   29.060137] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   29.062230] wlan0 direct probe responded
[   29.062232] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   29.063977] wlan0: authenticated
[   29.063980] wlan0: associate with AP 00:1f:1f:35:6d:60
[   29.066353] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   29.066356] wlan0: associated
[   37.377657] wlan0: deauthenticated (Reason: 1)
[   38.378015] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   38.380187] wlan0 direct probe responded
[   38.380191] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   38.381802] wlan0: authenticated
[   38.381805] wlan0: associate with AP 00:1f:1f:35:6d:60
[   38.384305] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   38.384308] wlan0: associated
[   45.276573] UDF-fs: No VRS found
[   45.276577] UDF-fs: No partition found (1)
[   45.367427] ISO 9660 Extensions: Microsoft Joliet Level 3
[   45.508312] ISO 9660 Extensions: RRIP_1991A
[   46.695104] wlan0: deauthenticated (Reason: 1)
[   47.695012] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   47.697133] wlan0 direct probe responded
[   47.697137] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   47.698875] wlan0: authenticated
[   47.698878] wlan0: associate with AP 00:1f:1f:35:6d:60
[   47.701245] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   47.701247] wlan0: associated
[   56.012427] wlan0: deauthenticated (Reason: 1)
[   57.013012] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   57.015081] wlan0 direct probe responded
[   57.015085] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   57.016950] wlan0: authenticated
[   57.016953] wlan0: associate with AP 00:1f:1f:35:6d:60
[   57.019326] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   57.019329] wlan0: associated
[   65.329879] wlan0: deauthenticated (Reason: 1)
[   66.330011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   66.332155] wlan0 direct probe responded
[   66.332159] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   66.334029] wlan0: authenticated
[   66.334032] wlan0: associate with AP 00:1f:1f:35:6d:60
[   66.336399] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   66.336403] wlan0: associated
[   74.647324] wlan0: deauthenticated (Reason: 1)
[   75.647136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   75.649232] wlan0 direct probe responded
[   75.649235] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   75.650973] wlan0: authenticated
[   75.650976] wlan0: associate with AP 00:1f:1f:35:6d:60
[   75.653225] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   75.653229] wlan0: associated
[   83.964771] wlan0: deauthenticated (Reason: 1)
[   84.965514] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   84.967692] wlan0 direct probe responded
[   84.967697] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   84.969424] wlan0: authenticated
[   84.969427] wlan0: associate with AP 00:1f:1f:35:6d:60
[   84.971675] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   84.971678] wlan0: associated
[   93.282219] wlan0: deauthenticated (Reason: 1)
[   94.282136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[   94.284256] wlan0 direct probe responded
[   94.284259] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[   94.285996] wlan0: authenticated
[   94.286000] wlan0: associate with AP 00:1f:1f:35:6d:60
[   94.288374] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[   94.288378] wlan0: associated
[  102.599569] wlan0: deauthenticated (Reason: 1)
[  103.599137] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  103.601330] wlan0 direct probe responded
[  103.601333] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  103.603073] wlan0: authenticated
[  103.603076] wlan0: associate with AP 00:1f:1f:35:6d:60
[  103.605448] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  103.605452] wlan0: associated
[  111.916992] wlan0: deauthenticated (Reason: 1)
[  112.916136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  112.918279] wlan0 direct probe responded
[  112.918283] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  112.920150] wlan0: authenticated
[  112.920153] wlan0: associate with AP 00:1f:1f:35:6d:60
[  112.922523] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  112.922527] wlan0: associated
[  121.234438] wlan0: deauthenticated (Reason: 1)
[  122.234139] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  122.236353] wlan0 direct probe responded
[  122.236357] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  122.238096] wlan0: authenticated
[  122.238100] wlan0: associate with AP 00:1f:1f:35:6d:60
[  122.240472] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  122.240475] wlan0: associated
[  130.551912] wlan0: deauthenticated (Reason: 1)
[  131.552012] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  131.554179] wlan0 direct probe responded
[  131.554183] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  131.555795] wlan0: authenticated
[  131.555798] wlan0: associate with AP 00:1f:1f:35:6d:60
[  131.558172] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  131.558175] wlan0: associated
[  139.869334] wlan0: deauthenticated (Reason: 1)
[  140.869137] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  140.871253] wlan0 direct probe responded
[  140.871256] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  140.872994] wlan0: authenticated
[  140.872997] wlan0: associate with AP 00:1f:1f:35:6d:60
[  140.875371] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  140.875374] wlan0: associated
[  149.186656] wlan0: deauthenticated (Reason: 1)
[  150.187014] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  150.189201] wlan0 direct probe responded
[  150.189204] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  150.190944] wlan0: authenticated
[  150.190947] wlan0: associate with AP 00:1f:1f:35:6d:60
[  150.193195] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  150.193199] wlan0: associated
[  158.504105] wlan0: deauthenticated (Reason: 1)
[  159.504012] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  159.507150] wlan0 direct probe responded
[  159.507153] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  159.508894] wlan0: authenticated
[  159.508898] wlan0: associate with AP 00:1f:1f:35:6d:60
[  159.511270] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  159.511274] wlan0: associated
[  167.821909] wlan0: deauthenticated (Reason: 1)
[  168.821137] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  168.823227] wlan0 direct probe responded
[  168.823230] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  168.824968] wlan0: authenticated
[  168.824971] wlan0: associate with AP 00:1f:1f:35:6d:60
[  168.828469] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  168.828472] wlan0: associated
[  177.139001] wlan0: deauthenticated (Reason: 1)
[  178.139013] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  178.141176] wlan0 direct probe responded
[  178.141179] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  178.142917] wlan0: authenticated
[  178.142920] wlan0: associate with AP 00:1f:1f:35:6d:60
[  178.145295] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  178.145298] wlan0: associated
[  186.456449] wlan0: deauthenticated (Reason: 1)
[  187.457011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  187.459249] wlan0 direct probe responded
[  187.459253] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  187.460867] wlan0: authenticated
[  187.460871] wlan0: associate with AP 00:1f:1f:35:6d:60
[  187.463243] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  187.463247] wlan0: associated
[  195.773773] wlan0: deauthenticated (Reason: 1)
[  196.773137] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  196.775326] wlan0 direct probe responded
[  196.775329] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  196.777066] wlan0: authenticated
[  196.777069] wlan0: associate with AP 00:1f:1f:35:6d:60
[  196.779603] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  196.779606] wlan0: associated
[  205.091220] wlan0: deauthenticated (Reason: 1)
[  206.091138] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  206.093275] wlan0 direct probe responded
[  206.093279] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  206.095016] wlan0: authenticated
[  206.095019] wlan0: associate with AP 00:1f:1f:35:6d:60
[  206.097394] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  206.097397] wlan0: associated
[  214.408668] wlan0: deauthenticated (Reason: 1)
[  215.408135] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  215.410223] wlan0 direct probe responded
[  215.410226] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  215.411966] wlan0: authenticated
[  215.411969] wlan0: associate with AP 00:1f:1f:35:6d:60
[  215.414343] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  215.414346] wlan0: associated
[  223.726616] wlan0: deauthenticated (Reason: 1)
[  224.726138] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  224.728298] wlan0 direct probe responded
[  224.728301] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  224.730039] wlan0: authenticated
[  224.730042] wlan0: associate with AP 00:1f:1f:35:6d:60
[  224.732417] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  224.732421] wlan0: associated
[  233.043610] wlan0: deauthenticated (Reason: 1)
[  234.044012] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  234.046125] wlan0 direct probe responded
[  234.046140] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  234.047865] wlan0: authenticated
[  234.047868] wlan0: associate with AP 00:1f:1f:35:6d:60
[  234.050116] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  234.050119] wlan0: associated
[  242.360932] wlan0: deauthenticated (Reason: 1)
[  243.361010] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  243.363196] wlan0 direct probe responded
[  243.363200] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  243.364813] wlan0: authenticated
[  243.364816] wlan0: associate with AP 00:1f:1f:35:6d:60
[  243.367191] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  243.367194] wlan0: associated
[  251.678380] wlan0: deauthenticated (Reason: 1)
[  252.679144] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  252.681290] wlan0 direct probe responded
[  252.681294] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  252.683138] wlan0: authenticated
[  252.683142] wlan0: associate with AP 00:1f:1f:35:6d:60
[  252.686134] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  252.686136] wlan0: associated
[  260.995829] wlan0: deauthenticated (Reason: 1)
[  261.996011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  261.998095] wlan0 direct probe responded
[  261.998099] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  261.999838] wlan0: authenticated
[  261.999841] wlan0: associate with AP 00:1f:1f:35:6d:60
[  262.002090] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  262.002094] wlan0: associated
[  270.313290] wlan0: deauthenticated (Reason: 1)
[  271.314011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  271.316170] wlan0 direct probe responded
[  271.316173] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  271.317913] wlan0: authenticated
[  271.317916] wlan0: associate with AP 00:1f:1f:35:6d:60
[  271.320164] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  271.320168] wlan0: associated
[  279.630701] wlan0: deauthenticated (Reason: 1)
[  280.631014] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  280.633244] wlan0 direct probe responded
[  280.633248] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  280.634862] wlan0: authenticated
[  280.634866] wlan0: associate with AP 00:1f:1f:35:6d:60
[  280.637239] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  280.637242] wlan0: associated
[  288.948054] wlan0: deauthenticated (Reason: 1)
[  289.948011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  289.950194] wlan0 direct probe responded
[  289.950198] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  289.951936] wlan0: authenticated
[  289.951939] wlan0: associate with AP 00:1f:1f:35:6d:60
[  289.954314] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  289.954317] wlan0: associated
[  298.265495] wlan0: deauthenticated (Reason: 1)
[  299.265136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  299.267267] wlan0 direct probe responded
[  299.267271] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  299.269011] wlan0: authenticated
[  299.269014] wlan0: associate with AP 00:1f:1f:35:6d:60
[  299.271387] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  299.271391] wlan0: associated
[  307.582943] wlan0: deauthenticated (Reason: 1)
[  308.582139] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  308.584217] wlan0 direct probe responded
[  308.584221] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  308.585961] wlan0: authenticated
[  308.585964] wlan0: associate with AP 00:1f:1f:35:6d:60
[  308.588337] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  308.588340] wlan0: associated
[  316.900393] wlan0: deauthenticated (Reason: 1)
[  317.900141] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  317.902295] wlan0 direct probe responded
[  317.902298] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  317.903909] wlan0: authenticated
[  317.903912] wlan0: associate with AP 00:1f:1f:35:6d:60
[  317.906287] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  317.906290] wlan0: associated
[  326.217840] wlan0: deauthenticated (Reason: 1)
[  327.217136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  327.219367] wlan0 direct probe responded
[  327.219371] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  327.221108] wlan0: authenticated
[  327.221111] wlan0: associate with AP 00:1f:1f:35:6d:60
[  327.223361] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  327.223364] wlan0: associated
[  335.535170] wlan0: deauthenticated (Reason: 1)
[  336.535136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  336.537316] wlan0 direct probe responded
[  336.537320] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  336.539059] wlan0: authenticated
[  336.539062] wlan0: associate with AP 00:1f:1f:35:6d:60
[  336.541310] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  336.541314] wlan0: associated
[  344.852610] wlan0: deauthenticated (Reason: 1)
[  345.852138] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  345.854265] wlan0 direct probe responded
[  345.854269] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  345.856009] wlan0: authenticated
[  345.856013] wlan0: associate with AP 00:1f:1f:35:6d:60
[  345.858260] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  345.858264] wlan0: associated
[  354.170057] wlan0: deauthenticated (Reason: 1)
[  355.170011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  355.172215] wlan0 direct probe responded
[  355.172218] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  355.173832] wlan0: authenticated
[  355.173835] wlan0: associate with AP 00:1f:1f:35:6d:60
[  355.176084] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  355.176087] wlan0: associated
[  363.487507] wlan0: deauthenticated (Reason: 1)
[  364.487136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  364.489290] wlan0 direct probe responded
[  364.489294] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  364.491158] wlan0: authenticated
[  364.491161] wlan0: associate with AP 00:1f:1f:35:6d:60
[  364.493534] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  364.493538] wlan0: associated
[  372.804958] wlan0: deauthenticated (Reason: 1)
[  373.804138] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  373.806241] wlan0 direct probe responded
[  373.806244] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  373.807982] wlan0: authenticated
[  373.807985] wlan0: associate with AP 00:1f:1f:35:6d:60
[  373.810359] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  373.810363] wlan0: associated
[  382.122279] wlan0: deauthenticated (Reason: 1)
[  383.122165] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  383.124314] wlan0 direct probe responded
[  383.124318] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  383.126055] wlan0: authenticated
[  383.126059] wlan0: associate with AP 00:1f:1f:35:6d:60
[  383.128434] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  383.128437] wlan0: associated
[  391.439725] wlan0: deauthenticated (Reason: 1)
[  392.439136] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  392.441263] wlan0 direct probe responded
[  392.441266] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  392.443006] wlan0: authenticated
[  392.443009] wlan0: associate with AP 00:1f:1f:35:6d:60
[  392.445382] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  392.445385] wlan0: associated
[  400.757180] wlan0: deauthenticated (Reason: 1)
[  401.758011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  401.760088] wlan0 direct probe responded
[  401.760092] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  401.761830] wlan0: authenticated
[  401.761833] wlan0: associate with AP 00:1f:1f:35:6d:60
[  401.764206] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  401.764209] wlan0: associated
[  410.074622] wlan0: deauthenticated (Reason: 1)
[  411.075014] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  411.077162] wlan0 direct probe responded
[  411.077166] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  411.078907] wlan0: authenticated
[  411.078910] wlan0: associate with AP 00:1f:1f:35:6d:60
[  411.081284] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  411.081288] wlan0: associated
[  419.392070] wlan0: deauthenticated (Reason: 1)
[  420.392011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  420.394237] wlan0 direct probe responded
[  420.394240] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  420.395854] wlan0: authenticated
[  420.395857] wlan0: associate with AP 00:1f:1f:35:6d:60
[  420.398105] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  420.398109] wlan0: associated
[  428.709393] wlan0: deauthenticated (Reason: 1)
[  429.711016] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  429.713256] wlan0 direct probe responded
[  429.713262] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  429.714804] wlan0: authenticated
[  429.714807] wlan0: associate with AP 00:1f:1f:35:6d:60
[  429.717180] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  429.717184] wlan0: associated
[  438.026842] wlan0: deauthenticated (Reason: 1)
[  439.027011] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  439.029261] wlan0 direct probe responded
[  439.029265] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  439.031011] wlan0: authenticated
[  439.031014] wlan0: associate with AP 00:1f:1f:35:6d:60
[  439.033254] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  439.033258] wlan0: associated
[  447.344289] wlan0: deauthenticated (Reason: 1)
[  448.345013] wlan0: direct probe to AP 00:1f:1f:35:6d:60 try 1
[  448.348208] wlan0 direct probe responded
[  448.348212] wlan0: authenticate with AP 00:1f:1f:35:6d:60
[  448.349953] wlan0: authenticated
[  448.349956] wlan0: associate with AP 00:1f:1f:35:6d:60
[  448.352329] wlan0: RX ReassocResp from 00:1f:1f:35:6d:60 (capab=0x411 status=0 aid=1)
[  448.352332] wlan0: associated
kevin@ubuntu:~$ 

kevin@ubuntu:~$ sudo ishw -c network
sudo: ishw: command not found
kevin@ubuntu:~$ sudo ishw -C network
sudo: ishw: command not found
kevin@ubuntu:~$ 

kevin@ubuntu:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

kevin@ubuntu:~$ lsb_ release -d
lsb_: command not found
kevin@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.10

kevin@ubuntu:~$ uname -mr
2.6.31-9-rt x86_64

kevin@ubuntu:~$ sudo / etc/ init .d/ networking restart
sudo: /: command not found
kevin@ubuntu:~$ sudo /etc /init .d /networking restart
sudo: /etc: command not found
kevin@ubuntu:~$ sudo /etc/init .d/networking restart
sudo: /etc/init: command not found




Many thanks.  Very impressed with Ubuntu so far.  What a great OS!!  Hoping to bin Windoze completely!!

---

### Post by 5MilesOut on 2010-01-23
Eveybody elses wireless OK in studio?

Thanks

---

### Post by buccaneerbob on 2010-02-06
Hum, I have the same problem. I was running version 8 WPA on the same hardware no problem. I upgraded wiping out the old now I a stuck. Under 8, I couldn't get Suse to work so I copied configuration files for Ubuntu to suse. So now I would copy a working config files from either another Ubuntu machine or do a sacrificial regular Ubuntu Install can copy the files over. The problem is all the WPA documentation I find talks about files that don't exist on my current install the configuration has changed significantly.  So can any one tells us or point us to the list of configuration files, specifically for 9.10 we would need to copy? 

Bob

---

### Post by bob1sparks on 2010-03-14
I copied the firmware files /lib/firmware from regular ubuntu to studio and it started to work. I got a clue about this from the dmesg output.

---

