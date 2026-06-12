---
title: "Lucid wireless problem with Buffalo router"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by simonjester on 2012-03-15
I am a long time LINUX user and have had difficulties with Wireless setups before (why is Ubuntu so poor with Wireless?  The network admin applet is not installed by default, really?)

I think the problem is my interfaces entry.I cannot get my wireless to negotiate with the router and get dhcp to work.    Here is the router info from iwlist scan

[B]Cell 02 - Address: 10:6F:3F:0C:07:96
Channel:11
Frequency:2.46.2 GHz (Channel 11)
Quality=50/70  Signal level=-60 dBm  
Encryption key:on
ESSID:"HERE"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000011bf39e7f3
Extra: Last beacon: 444ms ago
IE: Unknown: 001042554646414C4F2D3043303739365F47
IE: Unknown: 010882848B960C121824
IE: Unknown: 03010B
IE: Unknown: 200100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
[/B]

Here is my entry for /etc/network/intefaces

[B]wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-ssid HERE
wpa-psk "9758blablah"
[/B]

auto wlan0

---

