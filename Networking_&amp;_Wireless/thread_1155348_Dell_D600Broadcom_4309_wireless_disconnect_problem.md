---
title: "Dell D600/Broadcom 4309 wireless disconnect problems"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by drick on 2009-05-10
Hi,

I'm running Jaunty / 9.04 and am trying to figure out why my wireless connection keeps dropping when I'm more than 5 feet away from my wireless AP (Linksys WRT600N).

Per the HOWTO post, here is all the information requested:

1 ) Machine Brand and Model (PC/Laptop):

Dell D600

2 ) Wireless Brand, Model and Wireless Chipset:

$ lspci -nn
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

3 ) check interface:

$ iwconfig
 
wlan0     IEEE 802.11bg  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=90/100  Signal level:-42 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4 ) Check for modules:

$ lsmod |grep b43
b43                   131484  0 
mac80211              217208  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  1 b43 

5 ) Kernel boot messages

$ dmesg | grep -e ndis -e wlan
[ 24.384426] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 67.684472] wlan0: authenticate with AP 00:00::00:00:00
[ 67.686077] wlan0: authenticated
[ 67.686081] wlan0: associate with AP 00:00::00:00:00
[ 67.688498] wlan0: RX AssocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 67.688502] wlan0: associated
[ 67.689599] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 78.500030] wlan0: no IPv6 routers present
[ 355.264773] wlan0: deauthenticated
[ 356.264071] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 356.464061] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 356.695487] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 356.892079] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 358.464749] wlan0: authenticate with AP 00:00::00:00:00
[ 358.472170] wlan0: authenticate with AP 00:00::00:00:00
[ 358.475053] wlan0: authenticated
[ 358.475062] wlan0: associate with AP 00:00::00:00:00
[ 358.479608] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 358.479617] wlan0: associated
[ 428.616398] wlan0: deauthenticated
[ 429.616051] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 429.816066] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 430.016051] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 430.216052] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 431.776736] wlan0: authenticate with AP 00:00::00:00:00
[ 431.784149] wlan0: authenticate with AP 00:00::00:00:00
[ 431.984053] wlan0: authenticate with AP 00:00::00:00:00
[ 432.184070] wlan0: authenticate with AP 00:00::00:00:00
[ 432.384060] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 443.324754] wlan0: authenticate with AP 00:00::00:00:00
[ 443.348058] wlan0: authenticate with AP 00:00::00:00:00
[ 443.548077] wlan0: authenticate with AP 00:00::00:00:00
[ 443.748066] wlan0: authenticate with AP 00:00::00:00:00
[ 443.948072] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 447.012276] wlan0: authenticate with AP 00:00::00:00:00
[ 447.212071] wlan0: authenticate with AP 00:00::00:00:00
[ 447.412069] wlan0: authenticate with AP 00:00::00:00:00
[ 447.612070] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 457.020724] wlan0: authenticate with AP 00:00::00:00:00
[ 457.028138] wlan0: authenticate with AP 00:00::00:00:00
[ 457.228073] wlan0: authenticate with AP 00:00::00:00:00
[ 457.229630] wlan0: authenticated
[ 457.229639] wlan0: associate with AP 00:00::00:00:00
[ 457.428074] wlan0: associate with AP 00:00::00:00:00
[ 457.628072] wlan0: associate with AP 00:00::00:00:00
[ 457.828064] wlan0: association with AP 00:00::00:00:00 timed out
[ 468.640823] wlan0: authenticate with AP 00:00::00:00:00
[ 468.648151] wlan0: authenticate with AP 00:00::00:00:00
[ 468.848068] wlan0: authenticate with AP 00:00::00:00:00
[ 468.850474] wlan0: authenticated
[ 468.850484] wlan0: associate with AP 00:00::00:00:00
[ 469.048080] wlan0: associate with AP 00:00::00:00:00
[ 469.248054] wlan0: associate with AP 00:00::00:00:00
[ 469.448070] wlan0: association with AP 00:00::00:00:00 timed out
[ 480.152742] wlan0: authenticate with AP 00:00::00:00:00
[ 480.160173] wlan0: authenticate with AP 00:00::00:00:00
[ 480.360072] wlan0: authenticate with AP 00:00::00:00:00
[ 480.560059] wlan0: authenticate with AP 00:00::00:00:00
[ 480.760130] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 492.684260] wlan0: authenticate with AP 00:00::00:00:00
[ 492.884080] wlan0: authenticate with AP 00:00::00:00:00
[ 493.084069] wlan0: authenticate with AP 00:00::00:00:00
[ 493.284081] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 502.693354] wlan0: authenticate with AP 00:00::00:00:00
[ 502.716067] wlan0: authenticate with AP 00:00::00:00:00
[ 502.916051] wlan0: authenticate with AP 00:00::00:00:00
[ 503.116047] wlan0: authenticate with AP 00:00::00:00:00
[ 503.316066] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 514.208802] wlan0: authenticate with AP 00:00::00:00:00
[ 514.224123] wlan0: authenticate with AP 00:00::00:00:00
[ 514.424054] wlan0: authenticate with AP 00:00::00:00:00
[ 514.624062] wlan0: authenticate with AP 00:00::00:00:00
[ 514.824058] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 525.720774] wlan0: authenticate with AP 00:00::00:00:00
[ 525.744086] wlan0: authenticate with AP 00:00::00:00:00
[ 525.944069] wlan0: authenticate with AP 00:00::00:00:00
[ 525.952956] wlan0: authenticated
[ 525.952967] wlan0: associate with AP 00:00::00:00:00
[ 526.152071] wlan0: associate with AP 00:00::00:00:00
[ 526.352063] wlan0: associate with AP 00:00::00:00:00
[ 526.552075] wlan0: association with AP 00:00::00:00:00 timed out
[ 537.248730] wlan0: authenticate with AP 00:00::00:00:00
[ 537.248896] wlan0: authenticate with AP 00:00::00:00:00
[ 537.448083] wlan0: authenticate with AP 00:00::00:00:00
[ 537.648085] wlan0: authenticate with AP 00:00::00:00:00
[ 537.728601] wlan0: authenticated
[ 537.728614] wlan0: associate with AP 00:00::00:00:00
[ 537.928342] wlan0: associate with AP 00:00::00:00:00
[ 538.128238] wlan0: associate with AP 00:00::00:00:00
[ 538.328088] wlan0: association with AP 00:00::00:00:00 timed out
[ 548.776982] wlan0: authenticate with AP 00:00::00:00:00
[ 548.784156] wlan0: authenticate with AP 00:00::00:00:00
[ 548.984072] wlan0: authenticate with AP 00:00::00:00:00
[ 549.184074] wlan0: authenticate with AP 00:00::00:00:00
[ 549.384063] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 552.285465] wlan0: authenticate with AP 00:00::00:00:00
[ 552.300129] wlan0: authenticate with AP 00:00::00:00:00
[ 552.303563] wlan0: authenticated
[ 552.303572] wlan0: associate with AP 00:00::00:00:00
[ 552.500573] wlan0: associate with AP 00:00::00:00:00
[ 552.700055] wlan0: associate with AP 00:00::00:00:00
[ 552.900059] wlan0: association with AP 00:00::00:00:00 timed out
[ 563.800740] wlan0: authenticate with AP 00:00::00:00:00
[ 563.808314] wlan0: authenticate with AP 00:00::00:00:00
[ 563.811512] wlan0: authenticated
[ 563.811521] wlan0: associate with AP 00:00::00:00:00
[ 563.814794] wlan0: RX AssocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 563.814803] wlan0: associated
[ 685.300777] wlan0 direct probe responded
[ 685.300787] wlan0: authenticate with AP 00:00::00:00:00
[ 685.302346] wlan0: authenticated
[ 685.302352] wlan0: associate with AP 00:00::00:00:00
[ 685.309352] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 685.309358] wlan0: associated
[ 693.249068] wlan0: deauthenticated
[ 694.248035] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 694.448032] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 694.648044] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 694.848042] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 696.437665] wlan0: authenticate with AP 00:00::00:00:00
[ 696.452062] wlan0: authenticate with AP 00:00::00:00:00
[ 696.652047] wlan0: authenticate with AP 00:00::00:00:00
[ 696.852053] wlan0: authenticate with AP 00:00::00:00:00
[ 697.052045] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 707.944829] wlan0: authenticate with AP 00:00::00:00:00
[ 707.952074] wlan0: authenticate with AP 00:00::00:00:00
[ 708.152048] wlan0: authenticate with AP 00:00::00:00:00
[ 708.352039] wlan0: authenticate with AP 00:00::00:00:00
[ 708.553022] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 712.052214] wlan0: authenticate with AP 00:00::00:00:00
[ 712.252037] wlan0: authenticate with AP 00:00::00:00:00
[ 712.452047] wlan0: authenticate with AP 00:00::00:00:00
[ 712.453660] wlan0: authenticated
[ 712.453664] wlan0: associate with AP 00:00::00:00:00
[ 712.652053] wlan0: associate with AP 00:00::00:00:00
[ 712.852036] wlan0: associate with AP 00:00::00:00:00
[ 713.052033] wlan0: association with AP 00:00::00:00:00 timed out
[ 722.028499] wlan0: authenticate with AP 00:00::00:00:00
[ 722.028648] wlan0: authenticate with AP 00:00::00:00:00
[ 722.228038] wlan0: authenticate with AP 00:00::00:00:00
[ 722.428050] wlan0: authenticate with AP 00:00::00:00:00
[ 722.628059] wlan0: authentication with AP 00:00::00:00:00 timed out
[ 733.564785] wlan0: authenticate with AP 00:00::00:00:00
[ 733.572173] wlan0: authenticate with AP 00:00::00:00:00
[ 733.578618] wlan0: authenticated
[ 733.578630] wlan0: associate with AP 00:00::00:00:00
[ 733.581877] wlan0: RX AssocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 733.581886] wlan0: associated
[ 909.758795] wlan0: deauthenticated
[ 910.756036] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 910.956136] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 911.156049] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 911.356039] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 912.876454] wlan0: authenticate with AP 00:00::00:00:00
[ 912.884285] wlan0: authenticate with AP 00:00::00:00:00
[ 912.888538] wlan0: authenticated
[ 912.888542] wlan0: associate with AP 00:00::00:00:00
[ 913.088051] wlan0: associate with AP 00:00::00:00:00
[ 913.288042] wlan0: associate with AP 00:00::00:00:00
[ 913.488042] wlan0: association with AP 00:00::00:00:00 timed out
[ 924.390517] wlan0: authenticate with AP 00:00::00:00:00
[ 924.396125] wlan0: authenticate with AP 00:00::00:00:00
[ 924.402924] wlan0: authenticated
[ 924.402929] wlan0: associate with AP 00:00::00:00:00
[ 924.412246] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 924.412250] wlan0: associated
[ 1108.273774] wlan0: deauthenticated
[ 1109.272527] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 1109.472049] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 1109.672037] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 1109.872034] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 1111.444139] wlan0: authenticate with AP 00:00::00:00:00
[ 1111.452128] wlan0: authenticate with AP 00:00::00:00:00
[ 1111.458284] wlan0: authenticated
[ 1111.458289] wlan0: associate with AP 00:00::00:00:00
[ 1111.466342] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 1111.466346] wlan0: associated
[ 1231.479342] wlan0 direct probe responded
[ 1231.479351] wlan0: authenticate with AP 00:00::00:00:00
[ 1231.481223] wlan0: authenticated
[ 1231.481227] wlan0: associate with AP 00:00::00:00:00
[ 1231.483639] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 1231.483642] wlan0: associated
[ 1239.403408] wlan0: deauthenticated
[ 1240.400062] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 1240.403040] wlan0 direct probe responded
[ 1240.403044] wlan0: authenticate with AP 00:00::00:00:00
[ 1240.405125] wlan0: authenticated
[ 1240.405129] wlan0: associate with AP 00:00::00:00:00
[ 1240.407428] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 1240.407432] wlan0: associated
[ 1322.785545] wlan0: disassociating by local choice (reason=3)
[ 1327.852842] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1335.888939] wlan0: authenticate with AP 00:00::00:00:00
[ 1335.891042] wlan0: authenticated
[ 1335.891053] wlan0: associate with AP 00:00::00:00:00
[ 1335.895554] wlan0: RX AssocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 1335.895564] wlan0: associated
[ 1335.903875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1346.348029] wlan0: no IPv6 routers present
[ 5606.101351] wlan0: deauthenticated
[ 5607.100054] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 5607.300072] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 5607.500046] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 5607.700044] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 5609.296165] wlan0: authenticate with AP 00:00::00:00:00
[ 5609.296332] wlan0: authenticate with AP 00:00::00:00:00
[ 5609.496057] wlan0: authenticate with AP 00:00::00:00:00
[ 5609.583364] wlan0: authenticated
[ 5609.583374] wlan0: associate with AP 00:00::00:00:00
[ 5609.780070] wlan0: associate with AP 00:00::00:00:00
[ 5609.980046] wlan0: associate with AP 00:00::00:00:00
[ 5610.180047] wlan0: association with AP 00:00::00:00:00 timed out
[ 5620.804737] wlan0: authenticate with AP 00:00::00:00:00
[ 5620.820137] wlan0: authenticate with AP 00:00::00:00:00
[ 5620.864584] wlan0: authenticated
[ 5620.864595] wlan0: associate with AP 00:00::00:00:00
[ 5621.064069] wlan0: associate with AP 00:00::00:00:00
[ 5621.264068] wlan0: associate with AP 00:00::00:00:00
[ 5624.372302] wlan0: authenticate with AP 00:00::00:00:00
[ 5624.572054] wlan0: authenticate with AP 00:00::00:00:00
[ 5624.772058] wlan0: authenticate with AP 00:00::00:00:00
[ 5624.839015] wlan0: authenticated
[ 5624.839028] wlan0: associate with AP 00:00::00:00:00
[ 5624.842371] wlan0: RX AssocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 5624.842380] wlan0: associated
[ 5635.753393] wlan0: deauthenticated
[ 5636.752055] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 5636.952072] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 5637.152070] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 5637.352079] wlan0: direct probe to AP 00:00::00:00:00 timed out
[ 5638.880780] wlan0: authenticate with AP 00:00::00:00:00
[ 5638.880975] wlan0: authenticate with AP 00:00::00:00:00
[ 5638.884001] wlan0: authenticated
[ 5638.884038] wlan0: associate with AP 00:00::00:00:00
[ 5639.084068] wlan0: associate with AP 00:00::00:00:00
[ 5639.284065] wlan0: associate with AP 00:00::00:00:00
[ 5639.484048] wlan0: association with AP 00:00::00:00:00 timed out
[ 5650.396173] wlan0: authenticate with AP 00:00::00:00:00
[ 5650.404158] wlan0: authenticate with AP 00:00::00:00:00
[ 5650.406191] wlan0: authenticated
[ 5650.406203] wlan0: associate with AP 00:00::00:00:00
[ 5650.409065] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 5650.409075] wlan0: associated
[ 5834.617983] wlan0 direct probe responded
[ 5834.617999] wlan0: authenticate with AP 00:00::00:00:00
[ 5834.619886] wlan0: authenticated
[ 5834.619895] wlan0: associate with AP 00:00::00:00:00
[ 5834.625698] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 5834.625707] wlan0: associated
[ 5842.557795] wlan0: deauthenticated
[ 5843.556050] wlan0: direct probe to AP 00:00::00:00:00 try 1
[ 5843.756069] wlan0: direct probe to AP 00:00::00:00:00 try 2
[ 5843.956066] wlan0: direct probe to AP 00:00::00:00:00 try 3
[ 5843.959039] wlan0 direct probe responded
[ 5843.959049] wlan0: authenticate with AP 00:00::00:00:00
[ 5843.979862] wlan0: authenticated
[ 5843.979873] wlan0: associate with AP 00:00::00:00:00
[ 5844.176073] wlan0: associate with AP 00:00::00:00:00
[ 5844.215978] wlan0: RX ReassocResp from 00:00::00:00:00 (capab=0x411 status=0 aid=3)
[ 5844.215987] wlan0: associated

6 ) Network configuration

$ sudo lshw -C network

*-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.36 multicast=yes wireless=IEEE 802.11bg

7 ) Scan for networks:

$ iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:00:00:00:00:00
                    ESSID:"xxxxx"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=91/100  Signal level:-40 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: Unknown: 0005666B747367
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071300000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002332028185
                    Extra: Last beacon: 76ms ago


8 ) Ubuntu Version:

$ lsb_release -r
Release: 9.04

9 ) Kernel/architecture (including 32 vs. 64 bit):

32bit

$ uname -mr
2.6.28-11-generic i686

Any suggestion on how to fix this? I want to connect via wireless G only, and i can choose from WPA-TKIP or WPA2(personal)-AES encryption as my options on the laptop.

---

### Post by drick on 2009-05-10
$ dmesg | grep b43
[    3.279142] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   12.547619] b43-phy0: Broadcom 4306 WLAN found
[   23.836355] input: b43-phy0 as /devices/virtual/input/input9
[   23.868059] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   23.969960] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   24.049508] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   24.152269] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   24.296043] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   24.371060] Registered led device: b43-phy0::tx
[   24.371083] Registered led device: b43-phy0::rx
[   24.371104] Registered led device: b43-phy0::radio
[   24.384053] b43-phy0: Radio turned on by software
[ 1324.470968] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[ 1325.621015] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 1325.621035] b43-pci-bridge 0000:02:03.0: restoring config space at offset 0x1 (was 0x102, writing 0x106)
[ 1327.603680] input: b43-phy0 as /devices/virtual/input/input10
[ 1327.752049] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1327.806979] Registered led device: b43-phy0::tx
[ 1327.807028] Registered led device: b43-phy0::rx
[ 1327.807078] Registered led device: b43-phy0::radio

---

### Post by superprash2003 on 2009-05-11
it could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367) .. many are facing this issue

---

### Post by drick on 2009-05-11
it might be, although i believe that those are all different chipsets than the Broadcom that i have in the Dell.

---

