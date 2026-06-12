---
title: "Cannot access Wi-Fi channel 13"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by markytheone on 2009-12-12
Hi guys, I have an a/b/g/n/ card in server and I am trying to get it to register on Wi-Fi channel 13 (im in the UK) or use any of the 5 GHz channels. Here is my iw list:
> 
server1:~# iw list
Wiphy phy0
        Band 1:
                HT capabilities: 0x104e
                        * 20/40 MHz operation
                        * SM PS disabled
                        * 40 MHz short GI
                        * max A-MSDU len 3839
                        * DSSS/CCK 40 MHz
                HT A-MPDU factor: 0x0003 (65535 bytes)
                HT A-MPDU density: 0x0006 (8 usec)
                HT MCS set: ff ff 00 00 00 00 00 00 00 00 00 00 01 00 00 00
                HT TX/RX MCS rate indexes supported:
                        MCS index 0
                        MCS index 1
                        MCS index 2
                        MCS index 3
                        MCS index 4
                        MCS index 5
                        MCS index 6
                        MCS index 7
                        MCS index 8
                        MCS index 9
                        MCS index 10
                        MCS index 11
                        MCS index 12
                        MCS index 13
                        MCS index 14
                        MCS index 15
                Frequencies:
                        * 2412 MHz [1] (20.0 dBm)
                        * 2417 MHz [2] (20.0 dBm)
                        * 2422 MHz [3] (20.0 dBm)
                        * 2427 MHz [4] (20.0 dBm)
                        * 2432 MHz [5] (20.0 dBm)
                        * 2437 MHz [6] (20.0 dBm)
                        * 2442 MHz [7] (20.0 dBm)
                        * 2447 MHz [8] (20.0 dBm)
                        * 2452 MHz [9] (20.0 dBm)
                        * 2457 MHz [10] (20.0 dBm)
                        * 2462 MHz [11] (20.0 dBm)
                        * 2467 MHz [12] (disabled)
                        * 2472 MHz [13] (disabled)
                        * 2484 MHz [14] (disabled)
                Bitrates:
                        * 1.0 Mbps
                        * 2.0 Mbps (short preamble supported)
                        * 5.5 Mbps (short preamble supported)
                        * 11.0 Mbps (short preamble supported)
                        * 6.0 Mbps
                        * 9.0 Mbps
                        * 12.0 Mbps
                        * 18.0 Mbps
                        * 24.0 Mbps
                        * 36.0 Mbps
                        * 48.0 Mbps
                        * 54.0 Mbps
        Band 2:
                HT capabilities: 0x104e
                        * 20/40 MHz operation
                        * SM PS disabled
                        * 40 MHz short GI
                        * max A-MSDU len 3839
                        * DSSS/CCK 40 MHz
                HT A-MPDU factor: 0x0003 (65535 bytes)
                HT A-MPDU density: 0x0006 (8 usec)
                HT MCS set: ff ff 00 00 00 00 00 00 00 00 00 00 01 00 00 00
                HT TX/RX MCS rate indexes supported:
                        MCS index 0
                        MCS index 1
                        MCS index 2
                        MCS index 3
                        MCS index 4
                        MCS index 5
                        MCS index 6
                        MCS index 7
                        MCS index 8
                        MCS index 9
                        MCS index 10
                        MCS index 11
                        MCS index 12
                        MCS index 13
                        MCS index 14
                        MCS index 15
                Frequencies:
                        * 5180 MHz [36] (20.0 dBm) (passive scanning, no IBSS)
                        * 5200 MHz [40] (20.0 dBm) (passive scanning, no IBSS)
                        * 5220 MHz [44] (20.0 dBm) (passive scanning, no IBSS)
                        * 5240 MHz [48] (20.0 dBm) (passive scanning, no IBSS)
                        * 5260 MHz [52] (disabled)
                        * 5280 MHz [56] (disabled)
                        * 5300 MHz [60] (disabled)
                        * 5320 MHz [64] (disabled)
                        * 5500 MHz [100] (disabled)
                        * 5520 MHz [104] (disabled)
                        * 5540 MHz [108] (disabled)
                        * 5560 MHz [112] (disabled)
                        * 5580 MHz [116] (disabled)
                        * 5600 MHz [120] (disabled)
                        * 5620 MHz [124] (disabled)
                        * 5640 MHz [128] (disabled)
                        * 5660 MHz [132] (disabled)
                        * 5680 MHz [136] (disabled)
                        * 5700 MHz [140] (disabled)
                        * 5745 MHz [149] (20.0 dBm) (passive scanning, no IBSS)
                        * 5765 MHz [153] (20.0 dBm) (passive scanning, no IBSS)
                        * 5785 MHz [157] (20.0 dBm) (passive scanning, no IBSS)
                        * 5805 MHz [161] (20.0 dBm) (passive scanning, no IBSS)
                        * 5825 MHz [165] (20.0 dBm) (passive scanning, no IBSS)
                Bitrates:
                        * 6.0 Mbps
                        * 9.0 Mbps
                        * 12.0 Mbps
                        * 18.0 Mbps
                        * 24.0 Mbps
                        * 36.0 Mbps
                        * 48.0 Mbps
                        * 54.0 Mbps
        max # scan SSIDs: 4
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * monitor
                 * mesh point

Any ideas on how I can install CRDA? I have downloaded the source but I am stuck there.

---

### Post by bkratz on 2009-12-12
See this thread probably helpful

[http://ubuntuforums.org/showthread.php?t=1305148](http://ubuntuforums.org/showthread.php?t=1305148)

---

