---
title: "Consistently losing Wifi connection"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by umanohone on 2013-01-08
Hello,

The Wireless connection I am trying to debug is on Quantal 64-bit.

The Wifi adapter is a built in RTL8188CE on a Gateway NE56R03h Laptop.

I've tried using a hardcoded BSSID due to multiple access points on this floor, but only the closest AP works, so I figured it would be best to avoid connecting to weak Access Points. 

Security is WPA2 (Enterprise), PEAP, MSCHAPv2. 

This configuration produces a stable wireless connection under Windows 7, so I'm trying to determine the root cause of this issue. 

What gets to me is that it works for a while, and then for no obvious reason it stops working, with no obvious error message in the logs.

One thing I've noticed is that when connection goes down, the only packets being sent are a bunch of ARP requests.


Output from tcpdump:

01:58:18.538692 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28
01:58:19.538713 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28
01:58:20.538693 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28
01:58:21.594695 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28
01:58:22.594775 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28
01:58:23.594713 ARP, Request who-has gw-148.x.on.ca tell l-148-139.x.on.ca, length 28


[B]Suggestions for how to proceed with debugging this would be much appreciated. :D

I write software for a living and I have a pretty sweet development environment in Linux, but the flakey connection is a showstopper. So until I get this resolved I am stuck using Windows.[/B]


lsb_release -d:

Description:	Ubuntu 12.10


uname -mr:

3.5.0-21-generic x86_64


lspci -nn:

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)


lsmod:

rtl8192ce              53594  0 
rtl8192c_common        48779  1 rtl8192ce
rtlwifi                74705  1 rtl8192ce
mac80211              539908  3 rtl8192ce,rtl8192c_common,rtlwifi


iwconfig:

wlan0     IEEE 802.11bgn  ESSID:"Xxxxxxxx Secure Access"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:XX:XX:XX:XX:04   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0


Dmesg tail:

[ 7009.265070] wlan0: authenticate with 58:XX:XX:XX:XX:04
[ 7009.275805] wlan0: send auth to 58:XX:XX:XX:XX:04 (try 1/3)
[ 7009.277898] wlan0: authenticated
[ 7009.303211] wlan0: associate with 58:XX:XX:XX:XX:04 (try 1/3)
[ 7009.315447] wlan0: RX AssocResp from 58:XX:XX:XX:XX:04 (capab=0x431 status=0 aid=4)
[ 7009.315615] wlan0: associated
[ 7009.316042] cfg80211: Calling CRDA for country: CA
[ 7009.320009] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320014] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320016] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320018] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320020] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320022] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320024] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320026] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320027] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320030] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320031] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320033] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320035] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320037] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320039] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320041] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320043] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320045] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320046] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320049] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320050] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 7009.320052] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320054] cfg80211: Disabling freq 2467 MHz
[ 7009.320055] cfg80211: Disabling freq 2472 MHz
[ 7009.320057] cfg80211: Disabling freq 2484 MHz
[ 7009.320061] cfg80211: Regulatory domain changed to country: CA
[ 7009.320062] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7009.320064] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 7009.320066] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 7009.320068] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7009.320070] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7009.320072] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)


lshw -C network:

PCI (sysfs)  
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:XX:XX:XX:XX:20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-21-generic firmware=N/A ip=142.XX.XX.139 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:c0500000-c0503fff



iwlist scan:

wlan0     Scan completed :
          Cell 01 - Address: 58:XX:XX:XX:XX:04
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key: on
                    ESSID:"Xxxxxxxx Secure Access"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000079428fd064b
                    Extra: Last beacon: 191776ms ago
                    IE: Unknown: 0016536865726964616E2053656375726520416363657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B050200878D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E09008F000F00FF03590062722D73726E2D3574682D68616C6C000200003A
                    IE: Unknown: 9606004096000200
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401




Thanks for reading.

---

### Post by umanohone on 2013-01-10
I just thought I'd add:

The longest the connection has **stayed** UP is a couple of hours, but without fail, it eventually stops working.

Annoying. :lolflag:

---

### Post by umanohone on 2013-01-10
Just noticed these messages in syslog:

Jan 10 07:23:26 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:23:54 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:24:15 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:26:10 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:26:37 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:29:51 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:30:08 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4
Jan 10 07:31:18 xxxxxxxxx-NE56R wpa_supplicant[1001]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:XX:XX:XX:XX:04 reason=4

**So it appears that the connection is dropping quite frequently. Where to from here...?**

---

