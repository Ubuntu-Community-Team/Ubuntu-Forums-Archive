---
title: "RTL8188SU does not connect on Ubuntu 10.10"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by Aspire5570 on 2011-03-20
I am running Ubuntu 10.10 (2.6.35-28-generic) and I have a USB Wireless Card with a Realtek Chipset (RTL8188SU).  I downloaded the driver from the official website of Realtek; installed 8712u.ko, and moved the 8192sfw.bin into (/lib/firmware/RTL8192SU).

Now when I plug in my USB Wireless card; the indicator light will flash, the system will recognize the device:

*(Bus 001 Device 005: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter)

But it just will not connect. (Below is what I get from "dmesg"

[12721.586579] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 902b, size: 30, imemsize: 7408, sram size: 9688
[12721.587758] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[12721.591261] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[12721.591383] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[12721.592628] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[12721.593625] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[12721.593873] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[12721.593876] rtl819xU:FirmwareDownload92S(): Firmware Download Success
[12724.267262] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[12842.851434] Linking with Seednet WT II,channel:6, qos:0, myHT:1, networkHT:0, mode:6
[12843.605084] ===>ieee80211_associate_procedure_wq(), chan:6
[12843.643400] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[12843.657560] =================>ieee80211_authentication_req():auth->algorithm is 0
[12846.161040] Linking with Seednet WT II,channel:6, qos:0, myHT:1, networkHT:0, mode:6
[12846.161048] ===>ieee80211_associate_procedure_wq(), chan:6
[12846.199389] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[12846.214675] =================>ieee80211_authentication_req():auth->algorithm is 0
[12848.610056] alg name:WEP
[12848.610077] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 1, SECR_value: f
[12848.610290] rtl819xU:setKey(): dev: eb850000, EntryNo: 0, KeyIndex: 0, KeyType: 1, MacAddr: 00:00:00:00:00:00
[12848.614729] Linking with Seednet WT II,channel:6, qos:0, myHT:1, networkHT:0, mode:6
[12848.614742] Linking with Seednet WT II,channel:6, qos:0, myHT:1, networkHT:0, mode:6
[12848.616877] ===>ieee80211_associate_procedure_wq(), chan:6
[12848.659864] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[12848.674286] =================>ieee80211_authentication_req():auth->algorithm is 0

Any help is totally welcomed; I have spent the last 5 days trying to figure out why I can not connect this wireless card.:confused:

---

### Post by Dr_Frost on 2011-03-24
I just got and USB wifi home from DX, also that chipset.
Link: [http://www.dealextreme.com/p/super-mini-usb-2-0-802-11n-g-b-150mbps-wifi-wlan-wireless-network-adapter-35897](http://www.dealextreme.com/p/super-mini-usb-2-0-802-11n-g-b-150mbps-wifi-wlan-wireless-network-adapter-35897)

I finds it in LSUSB, and i can see it in the network icon (panel), but can't see any wifi networks.....

OS: Ubuntu 10.10 32-Bit

DMSEG:
```
[ 1233.664615]  RTUSB disconnect successfully
[ 1236.852563] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 1237.016620] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 1237.027409] ieee80211_crypt: registered algorithm 'NULL'
[ 1237.027417] ieee80211_crypt: registered algorithm 'TKIP'
[ 1237.027422] ieee80211_crypt: registered algorithm 'CCMP'
[ 1237.027427] ieee80211_crypt: registered algorithm 'WEP'
[ 1237.027431] 
[ 1237.027433] Linux kernel driver for RTL8192 based WLAN cards
[ 1237.027437] Copyright (c) 2007-2008, Realsil Wlan
[ 1237.027676] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[ 1237.027680] ==>RtInPipes:3  
[ 1237.027686] ==>RtOutPipes:4  6  13  
[ 1237.027696] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 1237.027702] 1  1  0  0  2  2  2  2  2  
[ 1237.173027] Dot11d_Init()
[ 1237.174977] usbcore: registered new interface driver rtl819xU
[ 1237.272353] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1237.272357] 
[ 1237.272777] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1237.272781] 
[ 1237.284974] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1237.284978] 
[ 1237.285481] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1237.285484] 
[ 1237.285490] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1237.285493] 
[ 1237.310631] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1237.310635] 
[ 1237.311046] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1237.311050] 
[ 1237.331486] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1237.331487] 
[ 1237.331734] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1237.331735] 
[ 1237.331737] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1237.331738] 
[ 1281.776862] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1281.776866] 
[ 1281.777102] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1281.777105] 
[ 1281.789105] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1281.789109] 
[ 1281.789346] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1281.789350] 
[ 1281.789355] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1281.789358] 
[ 1307.859270] usb 1-3: USB disconnect, address 3
[ 1307.868651] rtl819xU:=============>wlan driver to be removed
[ 1307.868656] 
[ 1307.879618] rtl819xU:wlan driver removed
[ 1307.879622] 
[ 1313.436057] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 1313.571478] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[ 1313.571484] ==>RtInPipes:3  
[ 1313.571490] ==>RtOutPipes:4  6  13  
[ 1313.571499] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 1313.571504] 1  1  0  0  2  2  2  2  2  
[ 1313.717051] Dot11d_Init()
[ 1313.743680] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1313.743681] 
[ 1313.743913] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1313.743914] 
[ 1313.755554] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1313.755559] 
[ 1313.756418] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1313.756422] 
[ 1313.756428] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1313.756431] 
[ 1313.778423] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1313.778424] 
[ 1313.778651] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1313.778652] 
[ 1313.789780] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1313.789781] 
[ 1313.790026] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1313.790027] 
[ 1313.790029] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1313.790030] 

```

---

### Post by bkratz on 2011-03-24
This thread may be of some help

[http://ubuntuforums.org/showthread.php?t=1667140](http://ubuntuforums.org/showthread.php?t=1667140)

---

### Post by Loganiii on 2011-03-25
Same issue...

Running Ubuntu 10.10 or 10.04, same issue...

My Realtek RTL8188CE wireless card installed in my new Toshiba Satellite, will not work.

It won't even see any networks, won't try. 

All I get is a red exclamation point, as if I don't even have wireless capability at all.

This is a major drag, because I bought this computer excited about going all Linux, and boom, here I sit, working in Windows 7... how embarrassing.  :(

---

