---
title: "ubuntu 12.04. No wireless after some times"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by lma33 on 2013-01-07
Hi,
Ubuntu 12.04-x86 3.2.0-35-generic-pae
USB-WiFi Adapter.
After the some big data (video, skipe) the adaptor can't connect to the router.

```

~$ lsusb
Bus 001 Device 003: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Imgo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:8C:3E:09:3F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:126  Invalid misc:62   Missed beacon:0

eth0      no wireless extensions.

~$ lsmod | grep -e rt2 -e rt3
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211


~$ dmesg
...
[   18.495986] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   20.020832] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[   20.024853] wlan0: authenticated
[   20.064839] wlan0: associate with 00:1e:8c:3e:09:3f (try 1)
[   20.067380] wlan0: RX AssocResp from 00:1e:8c:3e:09:3f (capab=0x411 status=0 aid=1)
[   20.067386] wlan0: associated
[   20.076109] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.024020] wlan0: no IPv6 routers present
[  315.147862] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 32628, forcing to 0
[  315.147869] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[  320.339540] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42597, forcing to 0
[  320.339546] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
...
[ 1053.180877] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1054.300844] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 35335, forcing to 0
[ 1054.300855] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1059.504076] ieee80211 phy0: wlan0: No probe response from AP 00:1e:8c:3e:09:3f after 500ms, disconnecting.
[ 1059.522551] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1059.522562] cfg80211: Restoring regulatory settings
[ 1059.522571] cfg80211: Calling CRDA to update world regulatory domain
[ 1059.535382] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1059.535393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
...
[ 1059.535547] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1059.535554] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1059.535561] cfg80211: World regulatory domain updated:
[ 1059.535565] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1059.535571] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1059.535577] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1059.535584] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1059.535590] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1059.535596] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1075.060245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1082.254619] usb 1-10: USB disconnect, device number 3
[ 1083.564047] usb 1-10: new high-speed USB device number 4 using ehci_hcd
[ 1083.832067] usb 1-10: reset high-speed USB device number 4 using ehci_hcd
[ 1083.991566] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1083.991576] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
...
[ 1083.991730] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1083.991737] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1083.994225] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[ 1083.996551] Registered led device: rt2800usb-phy1::radio
[ 1083.996651] Registered led device: rt2800usb-phy1::assoc
[ 1083.996747] Registered led device: rt2800usb-phy1::quality
[ 1084.981960] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1084.984374] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1088.994215] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[ 1088.997002] wlan0: authenticated
[ 1089.058210] wlan0: associate with 00:1e:8c:3e:09:3f (try 1)
[ 1089.061374] wlan0: RX AssocResp from 00:1e:8c:3e:09:3f (capab=0x411 status=0 aid=1)
[ 1089.061380] wlan0: associated
[ 1089.070059] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1099.888025] wlan0: no IPv6 routers present
[ 1107.761748] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy1
[ 1331.092148] phy1 -> rt2800usb_fill_rxdone: Error - Bad frame size 54562, forcing to 0
[ 1331.092155] phy1 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1331.434867] phy1 -> rt2800usb_fill_rxdone: Error - Bad frame size 16576, forcing to 0
[ 1331.434878] phy1 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1331.466926] phy1 -> rt2800usb_fill_rxdone: Error - Bad frame size 16576, forcing to 0
[ 1331.466937] phy1 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
...
[ 1345.558062] phy1 -> rt2800usb_fill_rxdone: Error - Bad frame size 58849, forcing to 0
[ 1345.558073] phy1 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1528.583260] phy1 -> rt2800usb_fill_rxdone: Error - Bad frame size 13222, forcing to 0
[ 1528.583266] phy1 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1571.512043] ieee80211 phy1: wlan0: No probe response from AP 00:1e:8c:3e:09:3f after 500ms, disconnecting.
[ 1571.525527] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1571.525538] cfg80211: Restoring regulatory settings
[ 1571.525546] cfg80211: Calling CRDA to update world regulatory domain
[ 1571.536589] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1571.536599] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1571.536605] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1571.536613] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
...
[ 1571.536753] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1571.536760] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1571.536767] cfg80211: World regulatory domain updated:
[ 1571.536771] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1571.536777] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1571.536783] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1571.536789] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1571.536796] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1571.536802] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1572.930819] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[ 1573.128062] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 2)
[ 1573.328043] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 3)
[ 1573.528052] wlan0: authentication with 00:1e:8c:3e:09:3f timed out
[ 1587.039483] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```The dmesg log is in the attachment.

Where I can find the solution of this problem?
[LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS][QUOTE] [/ QUOTE]
[/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » Russian[/LEFT]


[/COLOR][/CENTER]

---

### Post by lma33 on 2013-01-08
Adapter:
Linksys WUSB54GC  V3 Compact Wireless-G USB Network Adapter

Also from CD (rt2870.inf): 
```
[Linksys] 
; DisplayName               Section                 DeviceID 
; -----------               -------                 -------- 
%GenericWLAN.DeviceDesc%    = Ralink_3070.ndi,      USB\VID_1737&PID_0077 
 
```And release information:
```
~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS

```
*I don't know from where the text below:*

[LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS]1
[/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » Russian[/LEFT]


[/COLOR][/CENTER]

---

