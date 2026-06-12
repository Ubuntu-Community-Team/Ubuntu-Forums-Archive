---
title: "WiFi dropping and dropping speed"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by lemurid on 2010-02-25
As soon as i'm starting to copy a large file enough file (>700Mb) to my ubuntu box (connected to an Asus router via wifi) from a Windows 7 client (connected to router via ethernet cable) i get a dramatic drop in speed. upload starts at 1,0Mb/sec with a ping to ubuntu box at <1ms, and in 2 minutes it drops to 200kb/sec with a  ping of over 1000ms! The ping increases with every second in a linear progression.
To exlude router as a possible problem copying to a windows 7 notebook connected to router via wifi results in an average of 2,7Mb/sec with an average ping of 150ms. Any help will be appreciated.

MB Model: Asus P5B Deluxe wifi
OS: Ubuntu Server 9.10 + desktop installed
Wifi configured via GUI 

2. lsusb
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

3. wlan0     IEEE 802.11bg  ESSID:"removed"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: something   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4. lsmod
rtl8187                53604  0 
mac80211              209912  1 rtl8187
led_class               5256  1 rtl8187
eeprom_93cx6            2528  1 rtl8187

---

### Post by raffaele181188 on 2010-02-25
Maybe a driver issue.. I have a Ralink-based wifi card and it doesn't work very well with latest kernel... Post "dmesg | tail" and/or "dmesg | grep rtl"

---

### Post by lemurid on 2010-02-25
```
me@pc:~$ dmesg | grep rtl
[   16.325842] phy0: hwaddr 00:15:af:08:94:c2, RTL8187vB (default) V1 + rtl8225z2
[   16.452613] rtl8187: Customer ID is 0x00
[   16.452654] Registered led device: rtl8187-phy0::tx
[   16.452674] Registered led device: rtl8187-phy0::rx
[   16.452697] usbcore: registered new interface driver rtl8187
```

and tail gives this (rebooted to get the right one)

```
[   31.550778] wlan0: authenticate with AP 00:11:99:7e:28:b4
[   31.552650] wlan0: authenticated
[   31.552653] wlan0: associate with AP 00:11:99:7e:28:b4
[   31.554654] wlan0: RX AssocResp from 00:11:99:7e:28:b4 (capab=0x431 status=0 aid=2)
[   31.554657] wlan0: associated
[   31.556852] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.600101] cfg80211: Calling CRDA for country: DE
[   31.601496] cfg80211: Received country IE:
[   31.601498] cfg80211: Regulatory domain: DE
[   31.601500] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.601502] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   31.601503] cfg80211: CRDA thinks this should applied:
[   31.601504] cfg80211: Regulatory domain: DE
[   31.601506] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.601508] 	(2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   31.601509] 	(5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   31.601511] 	(5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   31.601512] cfg80211: We intersect both of these and get:
[   31.601514] cfg80211: Regulatory domain: 98
[   31.601515] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.601517] 	(2402000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   31.601520] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   31.601522] cfg80211: Current regulatory domain updated by AP to: DE
[   31.601523] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.601525] 	(2402000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.380020] wlan0: no IPv6 routers present

```

---

