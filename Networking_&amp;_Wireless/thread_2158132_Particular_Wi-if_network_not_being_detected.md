---
title: "Particular Wi-if network not being detected"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by 7Starphy on 2013-06-28
Hello friend,
I am using Ubuntu 12.10 . The Wi-fi at my house was working perfectly . But when I moved to another place , it is not detecting the Wi-fi there. It is detecting all other networks surrounding my house but doesn't detect the network in my current house. I haven't connected to this network before so it doesn't remember . The irony is that the same network is detected by my iPad and windows 7 in my other partition. Can anyone tell me why this particular network is not detected only by Ubuntu ?

---

### Post by coldraven on 2013-06-28
Have you tried "Connect to Hidden Wireless Network"?
Then enter the SSID found by your iPad and see if it connects.

---

### Post by chili555 on 2013-06-28
Please post:```
lspci -nn | grep 0280
sudo iwlist wlan0 scan
sudo iw reg get
```...assuming your wireless interface is wlan0; check:```
iwconfig
```If your wireless device is a single band 2.4 GHz card and the router is broadcasting on 5 GHz, I suppose that could be a factor. My N-protocol router switches bands at will.

---

### Post by 7Starphy on 2013-06-28
@coldraven - I already tried that , it is not working :( 

```

lspci -nn | grep 0280
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

Now the output for ```
sudo iwlist wlan0 scan
``` is

```

wlan0     Scan completed :
          Cell 01 - Address: 20:54:76:4D:C5:F2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"XPERIA sola_c8ca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 001058504552494120736F6C615F63386361
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435D0062322E00
          Cell 02 - Address: 98:FC:11:DA:EC:C6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DALELA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000644414C454C41
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 00:1E:58:C1:9F:26
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Ujjwal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0006556A6A77616C
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:1B:57:B4:63:87
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ITI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0003495449
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F4
          Cell 05 - Address: 00:25:9C:E7:6F:82
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"Home Wireless G310"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0012486F6D6520576972656C6573732047333130
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 00:1B:57:F2:61:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"bsmraji"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000762736D72616A69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
          Cell 07 - Address: 00:1E:40:53:55:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"vijay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 13172ms ago
                    IE: Unknown: 000576696A6179
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: AC:F1:DF:F0:BD:5D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Sachin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000653616368696E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051200000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:22:3F:03:D1:EA
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"AVI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0003415649
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F0101002CFF7F
                    IE: Unknown: DD1A00037F030100000000223F03D1EA06223F03D1EA64002C012C08

```

All the networks ,other than the network I want to connect appear above!

For ```
 sudo iw reg get 
```

```

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

---

### Post by chili555 on 2013-06-28
> Broadcom Corporation BCM43142 802.11b/g/n [[COLOR="#FF0000"]14e4:4365[/COLOR]]What driver is being used for this little beauty?```
lsmod | grep -e b43 -e wl -e brcmsmac
```I wonder if setting your country code might help:```
sudo iw reg set [COLOR="#FF0000"]US[/COLOR]
```If your country is not US, substitute the two-digit code from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Then try to scan again:```
sudo iwlist wlan0 scan
```Now does your network appear?

---

### Post by 7Starphy on 2013-06-28
I tried this 
```

lsmod | grep -e b43 -e wl -e brcmsmac
wl                   3074773  0 
cfg80211              206797  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl

```

I am living in India

So I tried 
```

sudo iw reg set IN

```

But I don't see the desired network. Like is it possible that I can't recognize a network because of country code, other networks seem to be working fine....I am having no idea what is going on here! 

So back to square one I guess :(

---

### Post by chili555 on 2013-06-28
*wl* is the correct driver for your device.> is it possible that I can't recognize a network because of country code, other networks seem to be working fineMy theory was that perhaps your desired network was broadcasting on a channel not availabe in the great and wonderful country of 00:> country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSSIn this context, 00 means default, one size fits all, maybe. If you run again:```
iw reg get
```You will see all these are different now. Let's have a look at:```
dmesg | grep -e wl -e cfg8
```I'm as puzzled as I was at post #2!

---

### Post by 7Starphy on 2013-06-28
Oh! Yeah the country code has changed from 00 to IN. 

Well ,for the other post
```

dmesg | grep -e wl -e cfg8
[   28.427738] cfg80211: Calling CRDA to update world regulatory domain
[   28.445798] wl: module license 'MIXED/Proprietary' taints kernel.
[   28.479104] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.479108] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479109] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.479111] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479113] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.479115] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479116] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.479118] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479119] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.479121] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479123] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.479125] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479126] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.479128] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479130] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.479132] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479133] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.479135] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479137] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.479138] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479140] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.479142] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479143] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   28.479145] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479147] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   28.479149] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479150] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   28.479152] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   28.479154] cfg80211: Disabling freq 5170 MHz
[   28.479155] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   28.479157] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479159] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   28.479160] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479162] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   28.479164] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479165] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   28.479167] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479169] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   28.479171] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479172] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   28.479174] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479176] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   28.479178] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479179] cfg80211: Disabling freq 5260 MHz
[   28.479180] cfg80211: Disabling freq 5280 MHz
[   28.479182] cfg80211: Disabling freq 5300 MHz
[   28.479183] cfg80211: Disabling freq 5320 MHz
[   28.479184] cfg80211: Disabling freq 5500 MHz
[   28.479185] cfg80211: Disabling freq 5520 MHz
[   28.479187] cfg80211: Disabling freq 5540 MHz
[   28.479188] cfg80211: Disabling freq 5560 MHz
[   28.479189] cfg80211: Disabling freq 5580 MHz
[   28.479190] cfg80211: Disabling freq 5600 MHz
[   28.479192] cfg80211: Disabling freq 5620 MHz
[   28.479193] cfg80211: Disabling freq 5640 MHz
[   28.479194] cfg80211: Disabling freq 5660 MHz
[   28.479195] cfg80211: Disabling freq 5680 MHz
[   28.479196] cfg80211: Disabling freq 5700 MHz
[   28.479198] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   28.479200] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479202] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   28.479203] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479205] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   28.479207] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479208] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   28.479210] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479212] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   28.479214] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.479215] cfg80211: Disabling freq 5920 MHz
[   28.479216] cfg80211: Disabling freq 5940 MHz
[   28.479218] cfg80211: Disabling freq 5960 MHz
[   28.479219] cfg80211: Disabling freq 5980 MHz
[   28.479220] cfg80211: Disabling freq 6000 MHz
[   28.479221] cfg80211: Disabling freq 6020 MHz
[   28.479222] cfg80211: Disabling freq 6040 MHz
[   28.479224] cfg80211: Disabling freq 6060 MHz
[   28.479225] cfg80211: Disabling freq 6080 MHz
[   28.480639] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   28.572693] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.20.55.19 (r300276)
[   28.594712] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.594716] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594718] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.594721] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594722] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.594724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594726] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.594728] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594730] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.594732] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594733] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.594735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594737] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.594739] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594740] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.594742] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594744] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.594745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594747] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.594749] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594750] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.594752] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594754] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   28.594756] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.594758] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   28.594759] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.594761] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   28.594763] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.594765] cfg80211: Disabling freq 5170 MHz
[   28.594766] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   28.594768] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594770] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   28.594771] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594773] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   28.594775] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594776] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   28.594778] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594779] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   28.594781] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594783] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   28.594785] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594786] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   28.594788] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594789] cfg80211: Disabling freq 5260 MHz
[   28.594790] cfg80211: Disabling freq 5280 MHz
[   28.594792] cfg80211: Disabling freq 5300 MHz
[   28.594793] cfg80211: Disabling freq 5320 MHz
[   28.594794] cfg80211: Disabling freq 5500 MHz
[   28.594795] cfg80211: Disabling freq 5520 MHz
[   28.594796] cfg80211: Disabling freq 5540 MHz
[   28.594798] cfg80211: Disabling freq 5560 MHz
[   28.594799] cfg80211: Disabling freq 5580 MHz
[   28.594800] cfg80211: Disabling freq 5600 MHz
[   28.594801] cfg80211: Disabling freq 5620 MHz
[   28.594803] cfg80211: Disabling freq 5640 MHz
[   28.594804] cfg80211: Disabling freq 5660 MHz
[   28.594805] cfg80211: Disabling freq 5680 MHz
[   28.594806] cfg80211: Disabling freq 5700 MHz
[   28.594808] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   28.594810] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594811] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   28.594813] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594815] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   28.594816] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594818] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   28.594820] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594821] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   28.594823] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594825] cfg80211: Disabling freq 5920 MHz
[   28.594826] cfg80211: Disabling freq 5940 MHz
[   28.594827] cfg80211: Disabling freq 5960 MHz
[   28.594828] cfg80211: Disabling freq 5980 MHz
[   28.594829] cfg80211: Disabling freq 6000 MHz
[   28.594831] cfg80211: Disabling freq 6020 MHz
[   28.594832] cfg80211: Disabling freq 6040 MHz
[   28.594833] cfg80211: Disabling freq 6060 MHz
[   28.594834] cfg80211: Disabling freq 6080 MHz
[   28.594838] cfg80211: World regulatory domain updated:
[   28.594840] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.594841] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594843] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.594845] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.594847] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.594849] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  277.476299] cfg80211: Calling CRDA for country: IN
[  277.481828] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  277.481831] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481834] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  277.481835] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481836] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  277.481838] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481839] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  277.481840] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481842] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  277.481843] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481844] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  277.481846] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481847] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  277.481849] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481851] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  277.481852] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481854] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  277.481856] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481857] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  277.481859] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481861] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  277.481862] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481863] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  277.481864] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481865] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  277.481866] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481867] cfg80211: Disabling freq 2484 MHz
[  277.481868] cfg80211: Disabling freq 5170 MHz
[  277.481869] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  277.481870] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481871] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[  277.481872] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481873] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  277.481874] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481875] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[  277.481876] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481887] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  277.481890] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481892] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  277.481894] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481896] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  277.481899] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481901] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  277.481904] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481906] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  277.481908] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481910] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  277.481913] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481915] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  277.481917] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481919] cfg80211: Disabling freq 5500 MHz
[  277.481921] cfg80211: Disabling freq 5520 MHz
[  277.481923] cfg80211: Disabling freq 5540 MHz
[  277.481925] cfg80211: Disabling freq 5560 MHz
[  277.481926] cfg80211: Disabling freq 5580 MHz
[  277.481928] cfg80211: Disabling freq 5600 MHz
[  277.481930] cfg80211: Disabling freq 5620 MHz
[  277.481932] cfg80211: Disabling freq 5640 MHz
[  277.481933] cfg80211: Disabling freq 5660 MHz
[  277.481935] cfg80211: Disabling freq 5680 MHz
[  277.481937] cfg80211: Disabling freq 5700 MHz
[  277.481939] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  277.481941] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481944] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  277.481946] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481948] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  277.481951] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481953] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  277.481955] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481958] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  277.481960] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  277.481962] cfg80211: Disabling freq 5920 MHz
[  277.481964] cfg80211: Disabling freq 5940 MHz
[  277.481966] cfg80211: Disabling freq 5960 MHz
[  277.481967] cfg80211: Disabling freq 5980 MHz
[  277.481969] cfg80211: Disabling freq 6000 MHz
[  277.481971] cfg80211: Disabling freq 6020 MHz
[  277.481972] cfg80211: Disabling freq 6040 MHz
[  277.481974] cfg80211: Disabling freq 6060 MHz
[  277.481976] cfg80211: Disabling freq 6080 MHz
[  277.481982] cfg80211: Regulatory domain changed to country: IN
[  277.481984] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  277.481986] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  277.481989] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  277.481991] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  277.481993] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1139.385763] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1139.385773] cfg80211: Restoring regulatory settings while preserving user preference for: IN
[ 1139.385780] cfg80211: Calling CRDA to update world regulatory domain
[ 1139.390283] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390290] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390293] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390296] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390298] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390336] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390351] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390359] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390363] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390367] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390375] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390387] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390388] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390390] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390392] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390395] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390398] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390400] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390401] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390403] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1139.390404] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390406] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1139.390407] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390408] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1139.390410] cfg80211: Disabling freq 5170 MHz
[ 1139.390411] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390412] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390414] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390415] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390416] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390418] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390419] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390420] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390422] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390423] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390426] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390444] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390455] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390466] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390477] cfg80211: Disabling freq 5260 MHz
[ 1139.390487] cfg80211: Disabling freq 5280 MHz
[ 1139.390496] cfg80211: Disabling freq 5300 MHz
[ 1139.390506] cfg80211: Disabling freq 5320 MHz
[ 1139.390511] cfg80211: Disabling freq 5500 MHz
[ 1139.390514] cfg80211: Disabling freq 5520 MHz
[ 1139.390517] cfg80211: Disabling freq 5540 MHz
[ 1139.390520] cfg80211: Disabling freq 5560 MHz
[ 1139.390522] cfg80211: Disabling freq 5580 MHz
[ 1139.390526] cfg80211: Disabling freq 5600 MHz
[ 1139.390529] cfg80211: Disabling freq 5620 MHz
[ 1139.390531] cfg80211: Disabling freq 5640 MHz
[ 1139.390534] cfg80211: Disabling freq 5660 MHz
[ 1139.390537] cfg80211: Disabling freq 5680 MHz
[ 1139.390540] cfg80211: Disabling freq 5700 MHz
[ 1139.390543] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390547] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390552] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390556] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390560] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390564] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390568] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390573] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390577] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.390581] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390584] cfg80211: Disabling freq 5920 MHz
[ 1139.390588] cfg80211: Disabling freq 5940 MHz
[ 1139.390591] cfg80211: Disabling freq 5960 MHz
[ 1139.390594] cfg80211: Disabling freq 5980 MHz
[ 1139.390597] cfg80211: Disabling freq 6000 MHz
[ 1139.390600] cfg80211: Disabling freq 6020 MHz
[ 1139.390603] cfg80211: Disabling freq 6040 MHz
[ 1139.390606] cfg80211: Disabling freq 6060 MHz
[ 1139.390609] cfg80211: Disabling freq 6080 MHz
[ 1139.390618] cfg80211: World regulatory domain updated:
[ 1139.390621] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1139.390625] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390630] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1139.390634] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1139.390638] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390643] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1139.390682] cfg80211: Calling CRDA for country: IN
[ 1139.395215] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395218] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395219] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395220] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395221] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395222] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395223] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395224] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395225] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395226] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395227] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395227] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395228] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395229] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395230] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395231] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395232] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395233] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395234] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395235] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395236] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395237] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395237] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395238] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395239] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395240] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395241] cfg80211: Disabling freq 2484 MHz
[ 1139.395242] cfg80211: Disabling freq 5170 MHz
[ 1139.395243] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395244] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395244] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395245] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395246] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395247] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395248] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395249] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395250] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395251] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395252] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395253] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395253] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395254] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395255] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395256] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395257] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395258] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395259] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395260] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395261] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395262] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395262] cfg80211: Disabling freq 5500 MHz
[ 1139.395263] cfg80211: Disabling freq 5520 MHz
[ 1139.395264] cfg80211: Disabling freq 5540 MHz
[ 1139.395264] cfg80211: Disabling freq 5560 MHz
[ 1139.395265] cfg80211: Disabling freq 5580 MHz
[ 1139.395266] cfg80211: Disabling freq 5600 MHz
[ 1139.395266] cfg80211: Disabling freq 5620 MHz
[ 1139.395267] cfg80211: Disabling freq 5640 MHz
[ 1139.395268] cfg80211: Disabling freq 5660 MHz
[ 1139.395268] cfg80211: Disabling freq 5680 MHz
[ 1139.395269] cfg80211: Disabling freq 5700 MHz
[ 1139.395270] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395271] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395272] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395273] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395274] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395275] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395275] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395276] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395277] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 1139.395278] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1139.395279] cfg80211: Disabling freq 5920 MHz
[ 1139.395280] cfg80211: Disabling freq 5940 MHz
[ 1139.395280] cfg80211: Disabling freq 5960 MHz
[ 1139.395281] cfg80211: Disabling freq 5980 MHz
[ 1139.395282] cfg80211: Disabling freq 6000 MHz
[ 1139.395282] cfg80211: Disabling freq 6020 MHz
[ 1139.395283] cfg80211: Disabling freq 6040 MHz
[ 1139.395284] cfg80211: Disabling freq 6060 MHz
[ 1139.395284] cfg80211: Disabling freq 6080 MHz
[ 1139.395287] cfg80211: Regulatory domain changed to country: IN
[ 1139.395288] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1139.395288] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1139.395289] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1139.395290] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1139.395291] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm)

```

So what to do next?

---

### Post by chili555 on 2013-06-28
> So what to do next? I think I would try the live CD for Ubuntu 13.04 and see if it works. You might also, if you have the right to do so, check in the router and change channels, make sure it's set to WPA2 only, not some mixed mode, turn off N speeds and experiment to see if any change allows you to connect.

I suspect 13.04 is going to do it.

I am getting very low on new ideas!

---

