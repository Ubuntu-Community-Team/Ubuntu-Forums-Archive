---
title: "Airlive X.usb - AP Mode"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-07-28
Does anybody know if the Airelive X.USB supports hostapd/AP Mode and 5Ghz?
[http://www.airlive.com/product/X.USB](http://www.airlive.com/product/X.USB)
[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-req-antennas](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-req-antennas)

I bought a Netgear WNDA3200 (Atheros AR9280) and it refuses to use any 5GHZ channels. I thought it was a Regulatory issue, but I've  tried both a recompile of crda and also a recompiled nl80211 module to each use a custom db.txt and it did nothing for my problem, must be a hardware limitation of the Netgear adapter.

---

### Post by bakegoodz on 2012-08-02
I got a reply from Think Penguin on this. The answer is no, but it may be hackable.

--Update-- I know how to hack it see post at [http://ubuntuforums.org/showthread.php?t=2032357](http://ubuntuforums.org/showthread.php?t=2032357)

> The default settings for AP mode are G-only. N is supported in non-AP
mode. I believe you can force it into N mode though and possibly use the
5Ghz frequency. I'm pretty confident we have had reports from other
customers of this working. Unfortunately we don't have the documentation
on this and it isn't officially supported by anybody. You can probably get
it working though if you post to the right mailing lists. We do have a
link to documentation on using hostapd to setup an access point that works
"perfectly" (as reported by numerous customers).

Here is the output you requested.

Wiphy phy2
    Band 1:
        Capabilities: 0x184e
            HT20/HT40
            SM Power Save disabled
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15, 32
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
            * 2467 MHz [12] (20.0 dBm) (passive scanning)
            * 2472 MHz [13] (20.0 dBm) (passive scanning)
            * 2484 MHz [14] (20.0 dBm) (passive scanning)
        Bitrates (non-HT):
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
        Capabilities: 0x184e
            HT20/HT40
            SM Power Save disabled
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15, 32
        Frequencies:
            * 4920 MHz [-16] (disabled)
            * 4940 MHz [-12] (disabled)
            * 4960 MHz [-8] (disabled)
            * 4980 MHz [-4] (disabled)
            * 5040 MHz [8] (disabled)
            * 5060 MHz [12] (disabled)
            * 5080 MHz [16] (disabled)
            * 5180 MHz [36] (30.0 dBm) (passive scanning, no IBSS)
            * 5200 MHz [40] (30.0 dBm) (passive scanning, no IBSS)
            * 5220 MHz [44] (30.0 dBm) (passive scanning, no IBSS)
            * 5240 MHz [48] (30.0 dBm) (passive scanning, no IBSS)
            * 5260 MHz [52] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5280 MHz [56] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5300 MHz [60] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5320 MHz [64] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5500 MHz [100] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5520 MHz [104] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5540 MHz [108] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5560 MHz [112] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5580 MHz [116] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5600 MHz [120] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5620 MHz [124] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5640 MHz [128] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5660 MHz [132] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5680 MHz [136] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5700 MHz [140] (30.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5745 MHz [149] (30.0 dBm) (passive scanning, no IBSS)
            * 5765 MHz [153] (30.0 dBm) (passive scanning, no IBSS)
            * 5785 MHz [157] (30.0 dBm) (passive scanning, no IBSS)
            * 5805 MHz [161] (30.0 dBm) (passive scanning, no IBSS)
            * 5825 MHz [165] (30.0 dBm) (passive scanning, no IBSS)
            * 5170 MHz [34] (30.0 dBm) (passive scanning, no IBSS)
            * 5190 MHz [38] (30.0 dBm) (passive scanning, no IBSS)
            * 5210 MHz [42] (30.0 dBm) (passive scanning, no IBSS)
            * 5230 MHz [46] (30.0 dBm) (passive scanning, no IBSS)
        Bitrates (non-HT):
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
         * Unknown mode (8)
         * Unknown mode (9)
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * Unknown command (68)
         * Unknown command (55)
         * Unknown command (57)
         * Unknown command (59)
         * Unknown command (67)
         * set_wiphy_netns
         * Unknown command (65)
         * Unknown command (66)
         * connect
         * disconnect

---

