---
title: "D-Link WDA-2320 + Ubuntu 10.04 = Problems Connecting..."
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by ahorne12 on 2011-02-02
Hello,

  I am trying to get my wireless card to work in my desktop, which I recently upgraded from 8.04 to 10.04.  It worked right out of the box in 8.04, but I'm finding it impossible to kick start in the newer LTS version.  My wirless card is:

D-link WDA2320

The Ubuntu wireless card Wiki sticky note at the top of this section supports my problems, stating: 

"Worked out of the box in 7.04, 7.10 and 8.04. WPA worked automatically in 7.10 and 8.04. In 9.04, works out of the box, but system hangs periodically with the ath5k driver; you must instead enable the madwifi driver in the Hardware Drivers dialog to get a stable system. In 9.10, does not work out of the box."  

Obviously, it does not give me any information on 10.04, so I'm not sure it is even possible to get working.  Assuming it would even work, I tried looking for madwifi in the Hardware drivers dialog (assuming they are referring to the option through System/Administration?), but cannot find it, or figure out how to search for it.

Following the rules suggested for resolving wireless problems, here is my info:

2 ) Wireless Brand, Model and Wireless Chipset (via lspci):

05:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

3 ) Check Interface (ifconfig):

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:7e:87:8b  
          inet6 addr: fe80::226:5aff:fe7e:878b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169588 (169.5 KB)  TX bytes:258443 (258.4 KB)

4 ) Check for modules (lsmod):

did not see any wlan modules, and none came upon searching (via lsmod | grep "wlan_module_name)

5 ) Kernel boot messages (dmesg)


[ 1295.500013] No probe response from AP 0a:bc:74:49:82:ab after 500ms, disconnecting.
[ 1297.213639] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1297.412024] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1297.612012] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1297.812012] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1308.970952] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1309.168017] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1309.368016] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1309.568011] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1311.713184] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1311.839005] wlan0: direct probe responded
[ 1311.839011] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 1)
[ 1312.036016] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 2)
[ 1312.236014] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 3)
[ 1312.312943] wlan0: authenticated
[ 1312.312965] wlan0: associate with AP 0a:bc:74:49:82:ab (try 1)
[ 1312.512015] wlan0: associate with AP 0a:bc:74:49:82:ab (try 2)
[ 1312.712016] wlan0: associate with AP 0a:bc:74:49:82:ab (try 3)
[ 1312.912013] wlan0: association with AP 0a:bc:74:49:82:ab timed out
[ 1348.979431] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1349.176021] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1349.376019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1349.576018] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1360.596294] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1360.796024] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1360.997877] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1361.196023] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1375.544192] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1375.744014] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1375.944014] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1376.144015] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1387.190004] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1387.388013] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1387.443761] wlan0: direct probe responded
[ 1387.443766] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 1)
[ 1387.640010] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 2)
[ 1387.840015] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 3)
[ 1388.040027] wlan0: authentication with AP 0a:bc:74:49:82:ab timed out
[ 1398.810528] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1399.008014] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1399.208013] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1399.408197] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1410.473506] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1410.672012] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1410.872015] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1411.072017] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1422.170534] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1422.368021] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1422.568016] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1422.768011] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1433.824820] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1434.024021] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1434.224081] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1434.424013] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1437.419366] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1437.616012] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1437.816017] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1437.868598] wlan0: direct probe responded
[ 1437.868601] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 1)
[ 1438.068010] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 2)
[ 1438.268015] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 3)
[ 1438.468013] wlan0: authentication with AP 0a:bc:74:49:82:ab timed out
[ 1448.920150] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1449.120012] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1449.320019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1449.520011] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1460.551931] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1460.748021] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1460.948019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1461.148160] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1478.560059] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1478.760022] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1478.960019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1479.160016] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1512.425604] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1512.624013] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1512.721340] wlan0: direct probe responded
[ 1512.721346] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 1)
[ 1512.920019] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 2)
[ 1513.120020] wlan0: authenticate with AP 0a:bc:74:49:82:ab (try 3)
[ 1513.320015] wlan0: authentication with AP 0a:bc:74:49:82:ab timed out
[ 1524.035944] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1524.232027] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1524.432019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1524.632018] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1542.032486] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1542.232021] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1542.432020] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1542.632011] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 1553.706271] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 1)
[ 1553.904022] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 2)
[ 1554.104019] wlan0: direct probe to AP 0a:bc:74:49:82:ab (try 3)
[ 1554.304018] wlan0: direct probe to AP 0a:bc:74:49:82:ab timed out
[ 2085.430267] eth1: link up.
[ 2085.431035] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2095.912009] eth1: no IPv6 routers present

This reflects some tries by entering MAC addresses I have written on a cheat sheet my friend gave me when she set up my wireless (LAN/WAN addresses)

6 ) Network configuration (sudo lshw -C network)

*-network:0             
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: wlan0
       version: 01
       serial: 00:26:5a:7e:87:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d1000000-d100ffff

7 ) Scan for networks (iwlist scan)

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:E5:EE:ED
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Internerd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000902def0e8b
                    Extra: Last beacon: 10976ms ago
                    IE: Unknown: 0009496E7465726E657264
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010006FF7F
                    IE: Unknown: DD0C00037F020101D80002A34000
          Cell 02 - Address: 00:24:01:F6:8C:78
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"anivison"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000018e2eea2
                    Extra: Last beacon: 10648ms ago
                    IE: Unknown: 0008616E697669736F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B051900000000000000000000000000000000000000
                    IE: Unknown: 3D160B051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
          Cell 03 - Address: 0A:BC:74:49:82:AB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ajhnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000504f891d188
                    Extra: Last beacon: 11400ms ago
                    IE: Unknown: 0006616A686E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180203F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

8 ) Ubuntu Version (lsb_release -d)

Description:	Ubuntu 10.04.1 LTS

9 ) Kernel/architecture (uname -mr)

2.6.32-28-generic i686

10 ) Restarting the network (sudo /etc/init.d/networking restart)

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]

***

So basically I'm really hoping something here triggers someone as to what may be wrong here, and whether I need to find a driver for the card, whether this card is toast for 10.04 and I need to buy a different brand, or whether it's just something stupid that I am overlooking (I am a relative ubuntu rookie).  I appreciate any help anyone is willing to give.  Thank you for reviewing my case :)

A

---

### Post by jsnelli2 on 2011-02-06
I installed the WDA-2320 in my desktop running 10.04 and had immediate internet connection wirelessly.

---

### Post by ahorne12 on 2011-02-08
Perhaps I wasn't clear in my problem.  I do have some wireless connection onto my secure network i.e. I can connect to my network, with reasonable strength (~65-70%); however, it is slow, often spontaneously disconnects, and occasionally has trouble reconnecting.  When connected, if I try to load a website, it takes minutes or more, and often fails to load the entire website (I guess it times out?).  I'm unsure of why this may be, especially given the last reply that this card can work in Ubuntu 10.04 right out of the box?  Am hoping someone has had reasonably similar problems, or may have an idea that could help.  Thanks,

A.

---

### Post by calast on 2011-03-19
I'm having some (possibly) similar issues under 10.10 with this card. It works just fine 90% of the time, so it's probably not something as serious as a bad configuration. But 10% of the time, when the system starts, it can't connect to my router. The network is fine - other machines have no trouble connecting. This machine worked flawlessly when it was a Windows machine. It just seems to have trouble under Ubuntu 10.10.

A restart always fixes the problem, but who wants to do that? I'm curious to see if someone has any suggestions on getting this machine to connect 100% of the time, like it used to. Some driver issue? Bad initialization? Why would it not be able to get a DHCP lease? The router lights indicate there are no active wireless connections when this happens (and all the other wireless machines are off), so as far as it is concerned, there's either no one out there asking for a lease, or else someone asked in a way that a DHCP lease was not granted.

Ideas, anyone?

---

### Post by NoonienSoong97 on 2012-12-27
I had no problems with the connection in ubuntu 10.10 but once I upgraded to 12.04 lts then I had the same issues posted on this thread.

---

