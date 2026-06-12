---
title: "Ubuntu 11.04 x64 as Wireless router"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by rolandcg on 2011-08-11
Hi All,
I want to set up my Laptop as a wireless router for my phone.
I did this with win 7 and connectify, since ad-hoc networking doesn't work with windows either.

I already put some work in this and found out that i would most likely have to use hostapd, since i can not create a working wireless network with ubuntu' 'create new wireless network'.

I also learned that the standard module is not appropriate for my wireless adapter, so I installed the latest linux-wireless module. that worked quit well, i can now connect reliably to my phone via a tethering application on my phone. but thats not what I want, since i cannot add a new dns server on my phone, so i just can tcp/ip my notebook.

I know that i would have to set my wlan0 to master mode, but i just got confused on my way, could somebody talk me through?

Thanks..

lspci:
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

 uname -r:
2.6.38-11-generic

lsmod | grep ath:
ath9k                 120567  0 
mac80211              308863  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              339053  2 ath9k,ath9k_common
ath                    23782  2 ath9k,ath9k_hw
cfg80211              196815  3 ath9k,mac80211,ath

hostapd /etc/hostapd/hostapd.conf:
Configuration file: /etc/hostapd/hostapd.conf
Line 2: invalid/unknown driver 'cfg80211'
1 errors found in configuration file '/etc/hostapd/hostapd.conf'
(happens with every driver name i can possibly think of, what is to put here?)

iw list:
Wiphy phy0
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
        HT TX/RX MCS rate indexes supported: 0-7
        Frequencies:
            * 2412 MHz [1] (14.0 dBm)
            * 2417 MHz [2] (14.0 dBm)
            * 2422 MHz [3] (14.0 dBm)
            * 2427 MHz [4] (14.0 dBm)
            * 2432 MHz [5] (14.0 dBm)
            * 2437 MHz [6] (14.0 dBm)
            * 2442 MHz [7] (14.0 dBm)
            * 2447 MHz [8] (14.0 dBm)
            * 2452 MHz [9] (14.0 dBm)
            * 2457 MHz [10] (14.0 dBm)
            * 2462 MHz [11] (14.0 dBm)
            * 2467 MHz [12] (14.0 dBm) (passive scanning)
            * 2472 MHz [13] (14.0 dBm) (passive scanning)
            * 2484 MHz [14] (17.0 dBm) (passive scanning)
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
         * managed ---> I cannot get it to master mode, what to do??
         * AP
         * AP/VLAN
         * WDS
         * monitor
         * mesh point
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

...

---

