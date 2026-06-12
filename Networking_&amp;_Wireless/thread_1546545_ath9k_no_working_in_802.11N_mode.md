---
title: "ath9k no working in 802.11N mode"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by blackmod on 2010-08-05
Hellooooo!

I'm trying to connect with atheros cards to a N router, but it works only in G mode.

I install latest ubuntu 10.04, updated to 2.6.35 kernel, install wireless-regdb, crda, compact-wireless as it is described here  ( [http://forum.aircrack-ng.org/index.php?topic=7826.0](http://forum.aircrack-ng.org/index.php?topic=7826.0) ), just to be sure it is not a regulatory problem.

But it still doesn't work on n, it goes maximum 700-800-900kb/s. iwconfig shows,

some info,

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:06.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:08.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 15)
00:0a.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0b.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)

```

```
[B]
wlan0     IEEE 802.11bgn  ESSID:"atheros"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: (deleted)  
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]
```

I have 2 atheros cards, AR9220 and AR5416, tried with both but same result.

```
iw list
Wiphy phy1
    Band 1:
        Capabilities: 0x11ce
            HT20/HT40
            SM Power Save disabled
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15
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
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (20.0 dBm)
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
        Capabilities: 0x11ce
            HT20/HT40
            SM Power Save disabled
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15
        Frequencies:
            * 5180 MHz [36] (20.0 dBm)
            * 5200 MHz [40] (20.0 dBm)
            * 5220 MHz [44] (20.0 dBm)
            * 5240 MHz [48] (20.0 dBm)
            * 5260 MHz [52] (20.0 dBm)
            * 5280 MHz [56] (20.0 dBm)
            * 5300 MHz [60] (20.0 dBm)
            * 5320 MHz [64] (20.0 dBm)
            * 5500 MHz [100] (20.0 dBm)
            * 5520 MHz [104] (20.0 dBm)
            * 5540 MHz [108] (20.0 dBm)
            * 5560 MHz [112] (20.0 dBm)
            * 5580 MHz [116] (20.0 dBm)
            * 5600 MHz [120] (20.0 dBm)
            * 5620 MHz [124] (20.0 dBm)
            * 5640 MHz [128] (20.0 dBm)
            * 5660 MHz [132] (20.0 dBm)
            * 5680 MHz [136] (20.0 dBm)
            * 5700 MHz [140] (20.0 dBm)
            * 5745 MHz [149] (20.0 dBm)
            * 5765 MHz [153] (20.0 dBm)
            * 5785 MHz [157] (20.0 dBm)
            * 5805 MHz [161] (20.0 dBm)
            * 5825 MHz [165] (20.0 dBm)
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
         * mesh point
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
         * Unknown command (55)
         * Unknown command (57)
         * Unknown command (59)
         * set_wiphy_netns
         * Unknown command (65)
         * connect
         * disconnect
Wiphy phy0
    Band 1:
        Capabilities: 0x104e
            HT20/HT40
            SM Power Save disabled
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15
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
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (20.0 dBm)
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
    max # scan SSIDs: 4
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point
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
         * Unknown command (55)
         * Unknown command (57)
         * Unknown command (59)
         * set_wiphy_netns
         * Unknown command (65)
         * connect
         * disconnect

```

```
lsmod | grep "ath9k"
ath9k                  96633  0 
ath9k_common            5955  1 ath9k
ath9k_hw              312131  2 ath9k,ath9k_common
ath                     1397  3 ath9k,ath9k_common,ath9k_hw
mac80211              233466  2 ath9k,ath9k_common
led_class               2633  1 ath9k
cfg80211              145292  3 ath9k,ath9k_common,mac80211

```

---

