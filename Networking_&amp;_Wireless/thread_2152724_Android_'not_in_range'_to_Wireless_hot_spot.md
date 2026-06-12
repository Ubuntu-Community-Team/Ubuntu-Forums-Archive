---
title: "Android 'not in range' to Wireless hot spot"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by Camy on 2013-06-08
Hey All
I'm a three day old Ubuntu user (ex Fedora) and loving it :)
 I've been trying to set up my computer as a wireless hotspot so that I can connect to the internet via wi-fi on my mobile, but all I get on it, is **'Not in range, secured with WEP'**

To set up the hotspot I followed this video:
[http://www.youtube.com/watch?v=gAvnh8TsFEU](http://www.youtube.com/watch?v=gAvnh8TsFEU)

I set the SSID, 
set the mode to Ad-hoc 
security: WEP 128 bit
set a password key
it is 'Shared to other computers'
Available to all users
And SAVED

Created new wireless network - ok

I can see the connection that I've just created and the wi-fi light comes on and my computer is picking up other wi-fi networks but my mobile keeps saying that it is not in range even though it is about 3 inches away.

I'm connected to the internet through a wired connection on my laptop and I can connect to other wi-fi routers using my phone.
I just can't get my phone to use my computer as a wi-fi hotspot.

I've even setup the network through settings, network, and add hotspot but still no luck.

I can't figure out what's wrong. It seems so simple :(

Any help appriciated.

---

### Post by scbingham on 2013-06-08
Mobiles won't connect to ad-hoc hotspots.
Follow this thread & its links.
[http://ubuntuforums.org/showthread.php?t=2149211](http://ubuntuforums.org/showthread.php?t=2149211)

Pay particular attention to establishing if your wireless adapter has the capabilities to act as an access point.

---

### Post by Camy on 2013-06-09
Installed hostapd after following this link
[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)

Ran
sudo hostapd ~/hostapd-test.conf
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=4 eloop_data=0x8b91910 user_data=0x8b91e80 handler=0x807c5e0
ELOOP: remaining socket: sock=6 eloop_data=0x8b93c88 user_data=(nil) handler=0x8086770

Then checked 'iw list' output
> Wiphy phy0
    Band 1:
        Frequencies:
            * 2412 MHz [1] (15.0 dBm)
            * 2417 MHz [2] (15.0 dBm)
            * 2422 MHz [3] (15.0 dBm)
            * 2427 MHz [4] (15.0 dBm)
            * 2432 MHz [5] (15.0 dBm)
            * 2437 MHz [6] (15.0 dBm)
            * 2442 MHz [7] (15.0 dBm)
            * 2447 MHz [8] (15.0 dBm)
            * 2452 MHz [9] (15.0 dBm)
            * 2457 MHz [10] (15.0 dBm)
            * 2462 MHz [11] (15.0 dBm)
            * 2467 MHz [12] (15.0 dBm) (passive scanning, no IBSS)
            * 2472 MHz [13] (15.0 dBm) (passive scanning, no IBSS)
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
        Frequencies:
            * 5170 MHz [34] (15.0 dBm) (passive scanning, no IBSS)
            * 5180 MHz [36] (15.0 dBm)
            * 5190 MHz [38] (15.0 dBm) (passive scanning, no IBSS)
            * 5200 MHz [40] (15.0 dBm)
            * 5210 MHz [42] (15.0 dBm) (passive scanning, no IBSS)
            * 5220 MHz [44] (15.0 dBm)
            * 5230 MHz [46] (15.0 dBm) (passive scanning, no IBSS)
            * 5240 MHz [48] (15.0 dBm)
            * 5260 MHz [52] (15.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5280 MHz [56] (15.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5300 MHz [60] (15.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5320 MHz [64] (15.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5500 MHz [100] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5520 MHz [104] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5540 MHz [108] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5560 MHz [112] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5580 MHz [116] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5600 MHz [120] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5620 MHz [124] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5640 MHz [128] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5660 MHz [132] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5680 MHz [136] (16.0 dBm) (passive scanning, no IBSS, radar detection)
            * 5700 MHz [140] (16.0 dBm) (passive scanning, no IBSS, radar detection)
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
    max scan IEs length: 2285 bytes
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
    Available Antennas: TX 0 RX 0
[B]    Supported interface modes:
         * IBSS
         * managed
         * monitor[/B]
    software interface modes (can always be added):
         * monitor
    interface combinations are not supported
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
         * join_mesh
         * set_tx_bitrate_mask
         * action
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * Unknown command (84)
         * Unknown command (87)
         * Unknown command (85)
         * testmode
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * managed: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP/VLAN: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * mesh point: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-client: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-GO: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
    Supported RX frame types:
         * IBSS: 0x00d0
         * managed: 0x0040 0x00d0
         * AP: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * AP/VLAN: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * mesh point: 0x00b0 0x00c0 0x00d0
         * P2P-client: 0x0040 0x00d0
         * P2P-GO: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
    Device supports RSN-IBSS.


Supported interface modes does not accept AP so it seems I can't do it on my computer which makes sense as I think I had tried it on Fedora too and couldn't connect either :(

Thanks for your help just the same.

---

### Post by scbingham on 2013-06-09
You might be able to install a different network adapter. I did but I can't get the adapter to work at all. I started another thread here, looking for assistance but so far no help at all. :(

---

### Post by Camy on 2013-06-10
Too busy to try that just yet.

Thanks for your help, much appreciated!

---

