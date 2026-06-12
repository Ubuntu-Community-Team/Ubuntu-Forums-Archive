---
title: "RT2870 Trouble."
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by 5fx on 2011-02-18
Hi, 

I bought a Linksys WUSB54GC-AS USB wifi stick, and on first boot of ubuntu 10.10 it auto detected it and i thought i was in for a real easy configuration process, so anyhow. [This is using the default rt2x000 drivers] I tried to connect to a network, sure, it worked after 5 minutes of continuos connecting and dropping, then when a connection is established its so flaky that im lucky to have it up for 2 minutes.

So I've installed the latest driver from Ralink's website, compiled them, did the usb id patch, installed the latest firmware too ( by moving it into /lib/firmware ) and then crossed my fingers and prayed. 

Same deal as before, with the rt2x000 drivers. Flaky connections, Doesnt even detect the network half of the time, and the best part about it is that it causes my system to freeze.

Here is the dmesg of the absolute chaos that is the Ralink drivers.

```
[  318.502736] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  318.786716] 
[  318.786760] 
[  318.786763] === pAd = ffffc9000261d000, size = 544384 ===
[  318.786767] 
[  318.790104] <-- RTMPAllocTxRxRingMemory, Status=0
[  318.790105] <-- RTMPAllocAdapterBlock, Status=0
[  325.493592] -->RTUSBVenderReset
[  325.496641] <--RTUSBVenderReset
[  333.406783] Key1Str is Invalid key length(0) or Type(0)
[  333.406915] Key2Str is Invalid key length(0) or Type(0)
[  333.407045] Key3Str is Invalid key length(0) or Type(0)
[  333.407178] Key4Str is Invalid key length(0) or Type(0)
[  333.409972] 1. Phy Mode = 5
[  333.410002] 2. Phy Mode = 5
[  333.652064] phy mode> Error! The chip does not support 5G band 6!
[  333.653364] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  333.951903] 3. Phy Mode = 9
[  334.238170] MCS Set = ff 00 00 00 01
[  334.279158] <==== rt28xx_init, Status=0
[  334.342135] 0x1300 = 00064300
[  334.541579] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[  341.697786] -->RTUSBVenderReset
[  341.699849] <--RTUSBVenderReset
[  349.576365] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  349.576408] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  349.578136] Key1Str is Invalid key length(0) or Type(0)
[  349.578261] Key2Str is Invalid key length(0) or Type(0)
[  349.578390] Key3Str is Invalid key length(0) or Type(0)
[  349.578524] Key4Str is Invalid key length(0) or Type(0)
[  349.581179] 1. Phy Mode = 5
[  349.581185] 2. Phy Mode = 5
[  349.820488] phy mode> Error! The chip does not support 5G band 6!
[  349.820602] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  350.126561] 3. Phy Mode = 9
[  350.345364] MCS Set = ff 00 00 00 01
[  350.384596] <==== rt28xx_init, Status=0
[  350.451862] 0x1300 = 00064300
[  354.329214] #
[  354.484796] #
[  355.829978] #
[  360.585319] #
[  360.623424] ra0: no IPv6 routers present
[  365.058924] #
[  365.997181] #
[  368.587832] #
[  378.186427] #
[  381.523746] #
[  386.181302] #
[  390.833541] #
[  392.476728] #

```

This just isnt good enough? Am I expected to have all these drivers be hit and miss? 

If anyone knows how to get this stick up and running let me know.

I'm at the point where im just going to buy another stick and forget about this POS.

---

