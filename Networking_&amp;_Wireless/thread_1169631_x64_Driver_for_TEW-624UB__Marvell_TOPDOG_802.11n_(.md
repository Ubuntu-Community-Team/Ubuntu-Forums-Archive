---
title: "x64 Driver for TEW-624UB / Marvell TOPDOG 802.11n (1286:2006) ?"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by 0graham0 on 2009-05-25
Hi,

I am running Ubuntu 9.04 x64 and it appears ndiswrapper does not like the windows driver for a Trendnet TEW-624UB Wireless USB adapter. The device ID for this adapter is 1286:2006 , which is also the ID for a Marvell TOPDOG 802.11 n adapter. Has anyone had any luck getting these cards to function? Relevant information I have found is below:

The info on the chipset from the ndiswrapper wiki:

> 
Card: Marvell 88W8360

      Chipset: Marvell 88W8360 TopDOG USB
      usbid: 1286:2006 “Marvell TOPDOG 802.11n WLAN Client Adaptors - USB”
      usbid: 1799:8051 “Belkin N1 Wireless USB Network Adapter"
      usbid: 13B1:0029 “Linksys Wireless-N USB Network Adapter”
      usbid: 0846:7100 “Netgear WN121T Wireless USB 2.0 Adapter"
      usbid: 07D1:3B11 “D-Link Wireless N USB Adapter DWA-130"
      usbid: 07D1:3B10 “D-Link RangeBooster N USB Adapter”
      usbid: 0B05:172A “ASUS 802.11n Network Adapter"
      usbid: 0B05:172B “ASUS 802.11n Network Adapter”
      usbid: 0411:00CA “Buffalo 802.11n Network Adapter”
      Driver: Mrv8360.inf / Mrv8360.sys, bundled Windows XP drivers on CD

      Other: (unknown vendor) Works perfectly with ndiswrapper 1.2+, tested from source with kernel 2.6.20 (vanilla) on Gentoo 2006.1; FWIW it also works with Project Evil on the BSD’s

Installing version 1.54 of ndiswrapper from the source, and attempting to use the Vista_x64 driver provided by Trendnet (netmw24c.inf) results in:```
sudo ndiswrapper -i netmw24c.inf
sudo ndiswrapper -l

netmw24c : driver installed
device (1286:2006) present
```

Then running the following command I get this info:```
sudo depmod -a
sudo modprobe ndiswrapper
tail /var/log/messages

[  124.644579] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  124.724339] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netmw24c
[  124.823053] usbcore: registered new interface driver ndiswrapper
```

Finally, following the troubleshooting guide I found the following information:```
dmesg | grep -e ndis -e wlan

[    7.817234] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    8.196024] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[    8.196033] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    8.196040] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    8.196046] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    8.196065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    8.196074] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    8.196080] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    8.196087] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    8.196093] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[    8.196101] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    8.196112] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[    8.196118] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    8.196125] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    8.196131] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[    8.196138] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    8.196144] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[    8.196150] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    8.196157] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[    8.196174] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[    8.196180] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[    8.196187] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[    8.196193] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    8.196212] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    8.196220] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[    8.196225] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[    8.196228] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw24c'
[    8.196569] ndiswrapper (load_wrap_driver:108): couldn't load driver netmw24c; check system log for messages from 'loadndisdriver'
[    8.196600] usbcore: registered new interface driver ndiswrapper

```

I've also tried the Windows XP trendnet driver and a couple of other drivers for some of the devices with the same chipset in the ndiswrapper wiki with no luck. However, I cannot find the mrv8360.inf that was reported as working in the wiki. I will continue trying the rest of the drivers in that list and will report back. Any help is greatly appreciated.

---

### Post by 0graham0 on 2009-05-25
I just finished testing each driver listed as using the same chipset from that ndiswrapper wiki post. Still no luck. Several of the drivers would install but ndiswrapper -l would not say device present. 

In the troubleshooting guide I noted there is a method to try and force ndiswrapper to use a certain driver. I was afraid of damaging my network adapter so I have not tried this yet.

Here is the results of my driver testing:

1. This driver gives me the problems detailed in my first forum post:

netmw24c.inf
Mrvw24C.sys
mrvw24c.cat 

Devices whose manufacturers offered these drivers were:

- usbid: 1286:2006 “Marvell TOPDOG 802.11n WLAN Client Adaptors USB”
- usbid: 0B05:172A “ASUS 802.11n Network Adapter" (ASUS WL-160N?)
- usbid: 13B1:0029 “Linksys Wireless-N USB Network Adapter” (WUSB300N)

2. The following devices all use these Vista x64 drivers. ndiswrapper does not detect a device present with this driver and my TEW624UB :

netr28ux.inf
netr28ux.sys
netr28ux.cat

Devices whose manufacturers offered these drivers were:

- usbid: 0B05:172B “ASUS 802.11n Network Adapter” (ASUS WL-160W?)
- usbid: 1799:8051 “Belkin N1 Wireless USB Network Adapter" (F4D8051 V3)
- usbid: 07D1:3B11 “D-Link Wireless N USB Adapter DWA-130 (Rev B)"
- usbid: 07D1:3B10 “D-Link RangeBooster N USB Adapter (DWA-140?)”

3. Again, ndiswrapper does not detect a device present with this driver and my TEW624UB :

NETUG300.INF
U2G300NB.sys
U2G300N.cat

This driver came from:

- usbid: 0411:00CA “Buffalo 802.11n Network Adapter” (Model # WLI-UC-G300N)

4. I also tried this XP64 driver and ndiswrapper did not detect a device present:

rt2870.inf
rt2870.sys
rt2870.cat

Driver from:

- usbid: 07D1:3B11 “D-Link Wireless N USB Adapter DWA-130 (Rev B)"

5. Finally the following devices had installers from which I could not extract drivers. I did not wrangle too long with the installers, just tried using Universal Extractor on them and checked the TEMP directory while trying an install.

- usbid: 0846:7100 “Netgear WN121T Wireless USB 2.0 Adapter" 
- usbid: 1799:8051 “Belkin N1 Wireless USB Network Adapter" (F4D8051 V2)

Any other ideas?  Any thought on trying to force ndiswrapper to use netr28ux.inf (detailed in #2 above)? Thanks.

---

### Post by tohms on 2009-05-26
Same exact error here, except with the Linksys adapter, which as you noted uses the same chipset. Do you know if ndiswrapper for sure works with 64 bit drivers? I dont have much experience so Im just wondering...

---

### Post by 0graham0 on 2009-05-26
The way I understand it ndiswrapper should work fine with 64-bit drivers as long as your OS is also 64-bit. If you have a 32-bit OS installed, then ndiswrapper would need 32-bit drivers.

---

### Post by 0graham0 on 2009-05-28
> 2. The following devices all use these Vista x64 drivers. ndiswrapper does not detect a device present with this driver and my TEW624UB :

netr28ux.inf
netr28ux.sys
netr28ux.cat

Devices whose manufacturers offered these drivers were:

- usbid: 0B05:172B “ASUS 802.11n Network Adapter” (ASUS WL-160W?)
- usbid: 1799:8051 “Belkin N1 Wireless USB Network Adapter" (F4D8051 V3)
- usbid: 07D1:3B11 “D-Link Wireless N USB Adapter DWA-130 (Rev B)"
- usbid: 07D1:3B10 “D-Link RangeBooster N USB Adapter (DWA-140?)”


I know my previous posts have been quite lengthy so I figured I would just put out this specific question: does anyone have any idea how dangerous it is to force ndiswrapper to try and use alternate drivers? I know there was some sort of disclaimer about ndiswrapper causing permanent damage to an adapter if it is forced to use the wrong driver. Is this just a disclaimer for rare situations or is it a bad idea to try and get my TEW-624UB adapter working using drivers for a different WLAN adapter with the same chipset (quoted above)? Thanks

---

