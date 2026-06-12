---
title: "Wireless connection keeps getting interrupted."
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by thebestofall007 on 2013-03-17
Hello, I am having an issue with my wifi connection to my router consistently getting disrupted every 4-5 or so minutes (but not all the time). When I first installed kubuntu, I didn't have this problem. I am using Kubuntu 12.04 on a macbook pro 4.1 laptop with the broadcom BCM4321 wireless card. I have tried: ```
sudo iwconfig eth1 power off
``` command, switching from network-manager to wicd network manager, resetting the router, tried making a script that disables wireless power saving that contains: ```
#!/bin/sh

/sbin/iwconfig eth1 power off
``` and placing in the /etc/pm/power.d folder and naming the script "wireless".

the output to the /var/log/syslog of when this event is happening is here:
```
Mar 17 14:41:16 lou-MacBookPro dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Mar 17 14:41:16 lou-MacBookPro dhclient: Copyright 2004-2011 Internet Systems Consortium.
Mar 17 14:41:16 lou-MacBookPro dhclient: All rights reserved.
Mar 17 14:41:16 lou-MacBookPro dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 17 14:41:16 lou-MacBookPro dhclient: 
Mar 17 14:41:16 lou-MacBookPro dhclient: Listening on LPF/eth1/00:21:e9:e2:f2:34
Mar 17 14:41:16 lou-MacBookPro dhclient: Sending on   LPF/eth1/00:21:e9:e2:f2:34
Mar 17 14:41:16 lou-MacBookPro dhclient: Sending on   Socket/fallback
Mar 17 14:41:16 lou-MacBookPro dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.779364] cfg80211: All devices are disconnected, going to restore regulatory settings
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.779376] cfg80211: Restoring regulatory settings
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.779384] cfg80211: Calling CRDA to update world regulatory domain
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.788998] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789002] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789004] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789007] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789009] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789012] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789014] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789016] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789018] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789021] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789023] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789025] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789028] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789030] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789032] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789035] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789037] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789042] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789044] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789047] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789049] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789051] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789054] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789056] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789059] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789061] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789066] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789068] cfg80211: Disabling freq 5160 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789069] cfg80211: Disabling freq 5170 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789071] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789074] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789076] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789079] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789081] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789083] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789085] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789088] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789090] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789093] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789095] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789097] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789099] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789102] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789104] cfg80211: Disabling freq 5250 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789105] cfg80211: Disabling freq 5260 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789107] cfg80211: Disabling freq 5270 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789108] cfg80211: Disabling freq 5280 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789110] cfg80211: Disabling freq 5290 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789111] cfg80211: Disabling freq 5300 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789113] cfg80211: Disabling freq 5310 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789114] cfg80211: Disabling freq 5320 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789115] cfg80211: Disabling freq 5330 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789117] cfg80211: Disabling freq 5340 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789118] cfg80211: Disabling freq 5350 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789120] cfg80211: Disabling freq 5360 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789121] cfg80211: Disabling freq 5370 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789123] cfg80211: Disabling freq 5380 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789124] cfg80211: Disabling freq 5390 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789126] cfg80211: Disabling freq 5400 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789127] cfg80211: Disabling freq 5410 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789129] cfg80211: Disabling freq 5420 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789130] cfg80211: Disabling freq 5430 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789132] cfg80211: Disabling freq 5440 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789133] cfg80211: Disabling freq 5450 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789134] cfg80211: Disabling freq 5460 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789136] cfg80211: Disabling freq 5470 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789137] cfg80211: Disabling freq 5480 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789139] cfg80211: Disabling freq 5490 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789140] cfg80211: Disabling freq 5500 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789142] cfg80211: Disabling freq 5510 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789143] cfg80211: Disabling freq 5520 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789145] cfg80211: Disabling freq 5530 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789146] cfg80211: Disabling freq 5540 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789148] cfg80211: Disabling freq 5550 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789149] cfg80211: Disabling freq 5560 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789151] cfg80211: Disabling freq 5570 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789152] cfg80211: Disabling freq 5580 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789153] cfg80211: Disabling freq 5590 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789155] cfg80211: Disabling freq 5600 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789156] cfg80211: Disabling freq 5610 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789158] cfg80211: Disabling freq 5620 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789159] cfg80211: Disabling freq 5630 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789161] cfg80211: Disabling freq 5640 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789162] cfg80211: Disabling freq 5650 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789164] cfg80211: Disabling freq 5660 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789165] cfg80211: Disabling freq 5670 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789167] cfg80211: Disabling freq 5680 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789168] cfg80211: Disabling freq 5690 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789170] cfg80211: Disabling freq 5700 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789171] cfg80211: Disabling freq 5710 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789172] cfg80211: Disabling freq 5720 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789174] cfg80211: Disabling freq 5725 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789176] cfg80211: Disabling freq 5730 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789177] cfg80211: Disabling freq 5735 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789178] cfg80211: Disabling freq 5740 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789180] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789183] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789185] cfg80211: Updating information on frequency 5750 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789188] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789190] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789192] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789194] cfg80211: Updating information on frequency 5760 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789197] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789199] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789201] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789203] cfg80211: Updating information on frequency 5770 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789206] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789208] cfg80211: Updating information on frequency 5775 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789211] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789213] cfg80211: Updating information on frequency 5780 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789215] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789217] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789220] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789222] cfg80211: Updating information on frequency 5790 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789225] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789227] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789229] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789231] cfg80211: Updating information on frequency 5800 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789234] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789236] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789238] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789241] cfg80211: Updating information on frequency 5810 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789243] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789245] cfg80211: Updating information on frequency 5815 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789248] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789250] cfg80211: Updating information on frequency 5820 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789253] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789255] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789257] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789259] cfg80211: Disabling freq 5830 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789261] cfg80211: Disabling freq 5840 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789262] cfg80211: Disabling freq 5850 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789263] cfg80211: Disabling freq 5860 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789265] cfg80211: Disabling freq 5870 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789266] cfg80211: Disabling freq 5880 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789268] cfg80211: Disabling freq 5890 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789269] cfg80211: Disabling freq 5900 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789270] cfg80211: Disabling freq 5910 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789272] cfg80211: Disabling freq 5920 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789273] cfg80211: Disabling freq 5930 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789275] cfg80211: Disabling freq 5940 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789276] cfg80211: Disabling freq 5950 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789277] cfg80211: Disabling freq 5960 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789279] cfg80211: Disabling freq 5970 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789280] cfg80211: Disabling freq 5980 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789282] cfg80211: Disabling freq 5990 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789283] cfg80211: Disabling freq 6000 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789284] cfg80211: Disabling freq 6010 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789286] cfg80211: Disabling freq 6020 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789287] cfg80211: Disabling freq 6030 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789289] cfg80211: Disabling freq 6040 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789290] cfg80211: Disabling freq 6050 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789292] cfg80211: Disabling freq 6060 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789293] cfg80211: Disabling freq 6070 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789294] cfg80211: Disabling freq 6080 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789296] cfg80211: Disabling freq 6090 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789297] cfg80211: Disabling freq 6100 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789299] cfg80211: Disabling freq 6110 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789300] cfg80211: Disabling freq 6120 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789301] cfg80211: Disabling freq 6130 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789303] cfg80211: Disabling freq 6140 MHz
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789311] cfg80211: World regulatory domain updated:
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789313] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789316] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789318] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789320] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789323] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6042.789325] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 17 14:41:17 lou-MacBookPro dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Mar 17 14:41:17 lou-MacBookPro dhclient: Copyright 2004-2011 Internet Systems Consortium.
Mar 17 14:41:17 lou-MacBookPro dhclient: All rights reserved.
Mar 17 14:41:17 lou-MacBookPro dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 17 14:41:17 lou-MacBookPro dhclient: 
Mar 17 14:41:17 lou-MacBookPro dhclient: Listening on LPF/eth0/00:1f:f3:52:1f:c7
Mar 17 14:41:17 lou-MacBookPro dhclient: Sending on   LPF/eth0/00:1f:f3:52:1f:c7
Mar 17 14:41:17 lou-MacBookPro dhclient: Sending on   Socket/fallback
Mar 17 14:41:17 lou-MacBookPro dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Mar 17 14:41:17 lou-MacBookPro dhclient: send_packet: Network is unreachable
Mar 17 14:41:17 lou-MacBookPro dhclient: send_packet: please consult README file regarding broadcast address.
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6043.018263] sky2 0000:0c:00.0: eth0: disabling interface
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6043.034127] sky2 0000:0c:00.0: eth0: enabling interface
Mar 17 14:41:17 lou-MacBookPro kernel: [ 6043.035223] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 17 14:41:59 lou-MacBookPro kernel: [ 6085.557977] applesmc: ALV1: read data fail

```

What it seems to be doing is disabling wireless channels whenever it feels like it, and consequently, my connection, so I have to go into wicd to connect again. It's getting obnoxious, and I have looked all over the internet for the solution but I can't find up-to-date information on this (as I have seen others have it with older versions of ubuntu/kubuntu have similar issues).

---

### Post by wildmanne39 on 2013-03-17
*Thread moved to **Networking & Wireless**.*

---

### Post by thebestofall007 on 2013-03-18
bump.

---

### Post by thebestofall007 on 2013-03-19
bump

---

### Post by Hadaka on 2013-03-19
Hi, please do..
```
lspci -nnk | grep -iA3 net
lsmod
```
post the results
thanks

---

### Post by thebestofall007 on 2013-03-20
lspci -nnk | grep -iA3 net:

```
lou@lou-MacBookPro:~$ lspci -nnk | grep -iA3 net
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)
        Subsystem: Apple Inc. Device [106b:008c]
        Kernel driver in use: wl
        Kernel modules: wl, ssb
0c:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
        Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
        Kernel driver in use: sky2
        Kernel modules: sky2
lou@lou-MacBookPro:~$ 
```

lsmod:
```
lou@lou-MacBookPro:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  0 
cifs                  287317  0 
snd_hrtimer            12744  1 
nfnetlink_queue        17882  1 
nfnetlink              14327  2 nfnetlink_queue
nf_conntrack_ipv4      19716  3 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_tcpudp              12603  7 
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
xt_iprange             12541  0 
xt_state               12578  3 
nf_conntrack           81926  2 nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  1 
xt_mark                12563  6 
xt_NFQUEUE             12726  3 
x_tables               29891  8 xt_tcpudp,iptable_filter,ip_tables,xt_iprange,xt_state,ipt_REJECT,xt_mark,xt_NFQUEUE
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
vboxdrv               320211  3 vboxpci,vboxnetadp,vboxnetflt
kvm_intel             137721  0 
kvm                   415550  1 kvm_intel
nfsd                  277884  2 
nfs                   356547  0 
lockd                  90326  2 nfsd,nfs
fscache                61529  1 nfs
parport_pc             32866  0 
ppdev                  17113  0 
auth_rpcgss            53380  2 nfsd,nfs
rfcomm                 47604  16 
bnep                   18281  2 
nfs_acl                12883  2 nfsd,nfs
binfmt_misc            17540  1 
sunrpc                245812  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
nvidia              11283521  52 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  5 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
lib80211_crypt_tkip    17390  0 
snd_hwdep              17764  1 snd_hda_codec
wl                   3074895  0 
snd_pcm                97275  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72627  0 
btusb                  18332  2 
snd_rawmidi            30748  1 snd_seq_midi
videodev               98259  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
bluetooth             180153  23 rfcomm,bnep,btusb
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
bcm5974                17399  0 
applesmc               19554  0 
snd                    79041  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev          13896  1 applesmc
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
apple_bl               13673  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
btrfs                 653005  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
vesafb                 13844  1 
hid_apple              13375  0 
usbhid                 47238  0 
hid                    99636  2 hid_apple,usbhid
firewire_ohci          41000  0 
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
video                  19651  0 
sky2                   59043  0 
lou@lou-MacBookPro:~$
```

---

### Post by thebestofall007 on 2013-03-20
bump.

---

### Post by thebestofall007 on 2013-03-23
bump

---

### Post by thebestofall007 on 2013-03-25
anyone...

---

### Post by Hadaka on 2013-03-25
Hi, sorry i havent responded, i forgot
to activate the notify. please do..
```
sudo modprobe -r ssb
 sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by thebestofall007 on 2013-03-25
> **Hadaka said:**
> Hi, sorry i havent responded, i forgot
to activate the notify. please do..
```
sudo modprobe -r ssb
 sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
thanks.


The sudo modprobe -r ssb and sudo modprobe wl commands had no output. Were they supposed to?

---

### Post by Hadaka on 2013-03-25
Hi, no output means it accepted the command.
please post the output of ..
```
lspci -nnk | grep -iA3 net
```
again please.
and have you booted, unpluged the wired
connection and tried wireless?

---

### Post by thebestofall007 on 2013-03-25
> **Hadaka said:**
> Hi, no output means it accepted the command.
please post the output of ..
```
lspci -nnk | grep -iA3 net
```
again please.
and have you booted, unpluged the wired
connection and tried wireless?


lspci -nnk | grep -iA3 net:

```
lou@lou-MacBookPro:~$ lspci -nnk | grep -iA3 net
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)
        Subsystem: Apple Inc. Device [106b:008c]
        Kernel driver in use: wl
        Kernel modules: wl, ssb
0c:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
        Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
        Kernel driver in use: sky2
        Kernel modules: sky2
lou@lou-MacBookPro:~$ 

```

Just got through rebooting and am using the wireless now as I type. It's still doing it, though.

---

### Post by Hadaka on 2013-03-25
Hi, looks like you may have at one time tried
to load the b43 driver...

 Kernel driver in use: wl         Kernel modules: wl, ssb
ssb and wl are conflicting...so lets
scrub out any of the b43 dependants and then
toss him and his buddies into the blackhole.
please do..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
you may get an error mesg. or a not installed on this...not to worry
then do.
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
add these 3 lines to the BOTTOM (last line) of the file..
```
blacklist b43
blacklist bcma
blacklist ssb
```
proof read...save..and close gedit
then..once again...please do..
```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
boot and test your wireless.
thanks.

---

### Post by thebestofall007 on 2013-03-25
I have a line in the blacklist file that reads:

# replaced by b43 and ssb.
blacklist bcm43xx

What are they doing with that?

---

### Post by Hadaka on 2013-03-26
I "think" that is created when you load the 
broadcome-kernel-source...sta..wl  driver.
but, for whatever reason the ssb did not get
blacklisted...so go ahead with the commands
i sent. 
thanks

---

### Post by thebestofall007 on 2013-03-26
It's still doing it, unfortunately.

---

### Post by wildmanne39 on 2013-03-26
Hi, I hope you do not mind me popping in I recommend removing the n from 802.11a/b/g/n to make it 802.11a/b/g in you router and see if that helps.
Thanks

---

### Post by thebestofall007 on 2013-03-26
> **Wild Man said:**
> Hi, I hope you do not mind me popping in I recommend removing the n from 802.11a/b/g/n to make it 802.11a/b/g in you router and see if that helps.
Thanks

How so?

---

### Post by wildmanne39 on 2013-03-26
Hi, you can usually go into your router settings by typing 192.168.0.1 then there should be a drop down screen that you can click on to change it.

The reason it may need changed is because many linux drivers do not work well with N speed.
Thanks

---

### Post by thebestofall007 on 2013-03-26
> **Wild Man said:**
> Hi, you can usually go into your router settings by typing 192.168.0.1 then there should be a drop down screen that you can click on to change it.

The reason it may need changed is because many linux drivers do not work well with N speed.
Thanks

oh, it's through the router.

---

### Post by wildmanne39 on 2013-03-26
Yes and you will need to be hard wired to your router to change the setting.
Thanks

---

### Post by thebestofall007 on 2013-03-26
> **Wild Man said:**
> Yes and you will need to be hard wired to your router to change the setting.
Thanks

Done that and changed setting to the 72 mbps setting. The max setting is 150 mbps.
I have included a screenshot of the interface of my netgear wnr-1000v3 router that shows the mode i am using if you need it.


Wish me luck. I'll chime in if it's a go or not.


Thanks.

---

### Post by wildmanne39 on 2013-03-26
I believe when you remove the n setting it should be set to 54mbs max.
Thanks

---

### Post by thebestofall007 on 2013-03-26
Reverted my router to 54mb/s mode.

It's going good so far...

We'll see later on how it goes tomorrow....

---

### Post by wildmanne39 on 2013-03-26
Fingers and toes crossed!!!

---

### Post by thebestofall007 on 2013-03-27
She's still cookin'. The reduced top speed isn't a bottleneck because my dsl connection is capped at 1mbps (100 kb/s up/download speed) anyway, so no harm no foul.

Is it true that the 802.11 n driver itself is at fault or is this a kernel issue or an issue with the netgear router I have?

---

### Post by wildmanne39 on 2013-03-27
Hi, yes some linux wireless drivers have issues connecting at N speed but as you said unless you have a real fast connection above 54 you do not need N speed.
Please mark the thread solved.
Thanks

---

### Post by dysonsphere232 on 2013-08-11
> **Wild Man said:**
> Hi, yes some linux wireless drivers have issues connecting at N speed but as you said unless you have a real fast connection above 54 you do not need N speed.
Please mark the thread solved.
Thanks

Thanks. Worked for me too. Ubuntu 12.04. 64-bit. MacBook Pro.

---

