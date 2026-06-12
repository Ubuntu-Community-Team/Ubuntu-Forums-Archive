---
title: "Inconsistent wireless connectivity, BCM4311"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by emanresu on 2009-03-24
greetings,

the wireless connection is very dodgy. i can only get a good connection 1 out of every 4 or 5 start ups and that's only if i've been logged into MS for a few days (dualboot laptop). the connection is 99% when i'm logged into MS.

the wireless router sits in my girlfriend's office and she actually works from there, so she needs space and i can't go and sit next to the router, which i shouldn't have to do anyway. if the phone rings, the cordless phone interrupts the connection and i have a hell of a time getting connected again. if the microwave is in use, the connection gets spotty. 

can someone tell me if i'm gonna have to keep dealing with the dodgy connection or can i do something to get more reliability? i've tried to read up and so i ran most of the lines through the terminal that the gurus have said to. here are the results:

```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:d4:f5:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

lspci -vv
 10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- 		FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- 	<PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

uname -a
 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

lsb_release -d
 Description:	Ubuntu 8.04.2

ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 00:17:08:43:41:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
 eth1      Link encap:Ethernet  HWaddr 00:14:a5:d4:f5:65  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fed4:f565/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28560130 (27.2 MB)  TX bytes:5038491 (4.8 MB)
 lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136298 (133.1 KB)  TX bytes:136298 (133.1 KB)
 wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-D4-F5-65-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
 lo        no wireless extensions.

 eth0      no wireless extensions.

 wmaster0  no wireless extensions.

 eth1      IEEE 802.11g  ESSID:"idaho"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:F4:F8:AC   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=86/100  Signal level=-48 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[   37.560543] b43-phy0: Broadcom 4311 WLAN found
[   37.603827] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   37.603850] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   59.350568] b43-phy0 debug: Chip initialized
[   59.350754] b43-phy0 debug: 32-bit DMA initialized
[   59.352046] Registered led device: b43-phy0:tx
[   59.352070] Registered led device: b43-phy0:rx
[   59.352088] Registered led device: b43-phy0:radio
[   59.352126] b43-phy0 debug: Wireless interface started
[   59.352130] b43-phy0 debug: Adding Interface type 2
[   79.162709] eth1: Initial auth_alg=0
[   79.162716] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   79.362486] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   79.562580] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   79.762291] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[   89.920571] eth1: Initial auth_alg=0
[   89.920579] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   90.119713] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   90.318474] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[   90.518368] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  100.182669] eth1: Initial auth_alg=0
[  100.182676] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  100.198949] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  100.238129] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  100.239436] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  100.865446] eth1: Initial auth_alg=0
[  100.865453] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  100.867907] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  100.867912] eth1: authenticated
[  100.867914] eth1: associate with AP 00:14:6c:f4:f8:ac
[  100.908784] eth1: RX AssocResp from 00:14:6c:f4:f8:ac (capab=0x411 status=0 aid=1)
[  100.908790] eth1: associated
[  100.908794] eth1: switched to short barker preamble (BSSID=00:14:6c:f4:f8:ac)
[  100.910392] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  102.902959] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=7)
[  102.902965] eth1: deauthenticated
[  102.906466] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=7)
[  102.957488] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=7)
[  103.034413] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.035838] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.036857] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.038250] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  103.635956] eth1: Initial auth_alg=0
[  103.635964] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.638994] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.640387] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  103.641543] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  103.644950] eth1: no IPv6 routers present
[  105.611392] eth1: Initial auth_alg=0
[  105.611399] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  105.614365] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  105.615675] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  105.616771] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  106.170744] eth1: authentication frame received from 00:14:6c:f4:f8:ac, but not in authenticate state - ignored
[  110.890238] eth1: Initial auth_alg=0
[  110.890245] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  111.089418] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  111.122908] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  111.122914] eth1: authenticated
[  111.122917] eth1: associate with AP 00:14:6c:f4:f8:ac
[  111.123835] eth1: authentication frame received from 00:14:6c:f4:f8:ac, but not in authenticate state - ignored
[  111.132343] eth1: authentication frame received from 00:14:6c:f4:f8:ac, but not in authenticate state - ignored
[  111.321712] eth1: associate with AP 00:14:6c:f4:f8:ac
[  111.521206] eth1: associate with AP 00:14:6c:f4:f8:ac
[  111.721118] eth1: association with AP 00:14:6c:f4:f8:ac timed out
[  112.120605] eth1: association frame received from 00:14:6c:f4:f8:ac, but not in associate state - ignored
[  112.411838] eth1: association frame received from 00:14:6c:f4:f8:ac, but not in associate state - ignored
[  112.441202] eth1: association frame received from 00:14:6c:f4:f8:ac, but not in associate state - ignored
[  112.574931] eth1: association frame received from 00:14:6c:f4:f8:ac, but not in associate state - ignored
[  121.657023] eth1: Initial auth_alg=0
[  121.657030] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  121.856161] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  122.056079] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  122.255965] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  132.416404] eth1: Initial auth_alg=0
[  132.416412] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  132.615561] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  132.815470] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  133.015368] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  143.352705] eth1: Initial auth_alg=0
[  143.352712] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  143.550992] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  143.750896] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  143.950799] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  154.108121] eth1: Initial auth_alg=0
[  154.108128] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  154.307298] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  154.507202] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  154.707105] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  161.799603] eth1: Initial auth_alg=0
[  161.799610] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  161.804263] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  161.805854] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  161.806889] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  162.687569] eth1: Initial auth_alg=0
[  162.687577] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  162.689111] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  162.690782] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  162.693266] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  164.725119] eth1: Initial auth_alg=0
[  164.725126] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  164.752696] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  164.757180] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  164.758776] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  167.387583] eth1: Initial auth_alg=0
[  167.387591] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  167.590658] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  167.790563] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  167.990468] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  168.827038] eth1: authentication frame received from 00:14:6c:f4:f8:ac, but not in authenticate state - ignored
[  177.326970] eth1: Initial auth_alg=0
[  177.326977] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  177.328472] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  177.328476] eth1: authenticated
[  177.328479] eth1: associate with AP 00:14:6c:f4:f8:ac
[  177.331028] eth1: RX AssocResp from 00:14:6c:f4:f8:ac (capab=0x411 status=0 aid=1)
[  177.331032] eth1: associated
[  177.331036] eth1: switched to short barker preamble (BSSID=00:14:6c:f4:f8:ac)
[  177.332406] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  186.009212] eth1: no IPv6 routers present
[  235.732439] eth1: No ProbeResp from current AP 00:14:6c:f4:f8:ac - assume out of range
[  235.765039] eth1: Initial auth_alg=0
[  235.765046] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  235.769646] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  235.774916] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  235.779480] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  238.319311] eth1: Initial auth_alg=0
[  238.319317] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  238.334507] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  238.349720] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  238.364068] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  240.053471] eth1: Initial auth_alg=0
[  240.053478] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  240.117404] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  240.149204] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  240.176163] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  241.517619] eth1: Initial auth_alg=0
[  241.517626] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  241.541869] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  241.572942] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  241.597379] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  244.233198] eth1: Initial auth_alg=0
[  244.233205] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  244.257736] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  244.282001] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  244.308867] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  245.588571] eth1: Initial auth_alg=0
[  245.588578] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  245.591071] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  245.591076] eth1: authenticated
[  245.591078] eth1: associate with AP 00:14:6c:f4:f8:ac
[  245.613876] eth1: associate with AP 00:14:6c:f4:f8:ac
[  245.644414] eth1: associate with AP 00:14:6c:f4:f8:ac
[  245.691777] eth1: association with AP 00:14:6c:f4:f8:ac timed out
[  246.423353] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=15)
[  246.423360] eth1: deauthenticated
[  247.921566] eth1: Initial auth_alg=0
[  247.921573] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  247.938787] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  247.959788] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  247.961772] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  247.961777] eth1: authenticated
[  247.961780] eth1: associate with AP 00:14:6c:f4:f8:ac
[  247.976617] eth1: associate with AP 00:14:6c:f4:f8:ac
[  247.988109] eth1: associate with AP 00:14:6c:f4:f8:ac
[  248.004395] eth1: association with AP 00:14:6c:f4:f8:ac timed out
[  250.345499] eth1: Initial auth_alg=0
[  250.345506] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  250.346964] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  250.346969] eth1: authenticated
[  250.346972] eth1: associate with AP 00:14:6c:f4:f8:ac
[  250.362558] eth1: associate with AP 00:14:6c:f4:f8:ac
[  250.363906] eth1: RX ReassocResp from 00:14:6c:f4:f8:ac (capab=0x411 status=0 aid=1)
[  250.363911] eth1: associated
[  250.363916] eth1: switched to short barker preamble (BSSID=00:14:6c:f4:f8:ac)
[  251.650825] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=7)
[  251.650830] eth1: deauthenticated
[  251.881499] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  251.882059] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  251.882064] eth1: authenticated
[  251.882067] eth1: associate with AP 00:14:6c:f4:f8:ac
[  251.885087] eth1: RX ReassocResp from 00:14:6c:f4:f8:ac (capab=0x411 status=0 aid=1)
[  251.885094] eth1: associated
[  251.885099] eth1: switched to short barker preamble (BSSID=00:14:6c:f4:f8:ac)
[  274.451210] eth1: RX deauthentication from 00:14:6c:f4:f8:ac (reason=7)
[  274.451216] eth1: deauthenticated
[  274.784984] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  274.787593] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  274.787599] eth1: authenticated
[  274.787602] eth1: associate with AP 00:14:6c:f4:f8:ac
[  274.848151] eth1: associate with AP 00:14:6c:f4:f8:ac
[  274.896773] eth1: associate with AP 00:14:6c:f4:f8:ac
[  274.951215] eth1: association with AP 00:14:6c:f4:f8:ac timed out
[  277.619162] eth1: Initial auth_alg=0
[  277.619170] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  277.681447] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  277.745008] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  277.798477] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  281.413681] eth1: Initial auth_alg=0
[  281.413688] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  281.462652] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  281.537323] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  281.592763] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  284.528498] eth1: Initial auth_alg=0
[  284.528506] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  284.556085] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  284.570859] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  284.619951] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  288.050029] eth1: Initial auth_alg=0
[  288.050037] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  288.064196] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  288.094643] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  288.114560] eth1: authentication with AP 00:14:6c:f4:f8:ac timed out
[  289.668874] eth1: authentication frame received from 00:14:6c:f4:f8:ac, but not in authenticate state - ignored
[  290.282212] eth1: Initial auth_alg=0
[  290.282220] eth1: authenticate with AP 00:14:6c:f4:f8:ac
[  290.323068] eth1: RX authentication from 00:14:6c:f4:f8:ac (alg=0 transaction=2 status=0)
[  290.323075] eth1: authenticated
[  290.323078] eth1: associate with AP 00:14:6c:f4:f8:ac
[  290.330045] eth1: associate with AP 00:14:6c:f4:f8:ac
[  290.336193] eth1: RX AssocResp from 00:14:6c:f4:f8:ac (capab=0x411 status=0 aid=1)
[  290.336199] eth1: associated
[  290.336204] eth1: switched to short barker preamble (BSSID=00:14:6c:f4:f8:ac)

lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:d4:f5:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11g

iwlist scan
 lo        Interface doesn't support scanning.

 eth0      Interface doesn't support scanning.

 wmaster0  Interface doesn't support scanning.

 eth1      No scan results

```

---

### Post by Ayuthia on 2009-03-24
Can you let us know which version of Ubuntu you are using?  I have the same chipset and similar issues with the microwave.  However, my signal has not been too bad.

---

### Post by emanresu on 2009-03-25
Ayuthia,

sorry, i thought i had covered all the bases.
i'm using version 8.04.

---

### Post by Ayuthia on 2009-03-25
Actually, it is my fault.  I did not see the uname -a info that you posted.  You might try and see if you can use the Broadcom STA module and see if it makes a difference.  You should be able to find it in System->Administration->Hardware Drivers.  You will need to disable the b43 module.  If it does not work on start up, try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by emanresu on 2009-03-26
Ayuthia,

it figures that i post about this issue after months of dealing with it and now, i've had 3 days of no problems. 

i don't know if this actually fixed anything but so far it seems to work. before i suspend the computer, i right-click on the network icon and disable the wireless networking. then when i start up from suspend, i enable wireless network. i don't know if this solve everything, because i have had problems getting a connection from a fresh startup/restart as well, but for now, since the problem's not duplicating, i worry less about it.

---

