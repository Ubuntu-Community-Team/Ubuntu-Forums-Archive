---
title: "Wifi stopped connecting to my primary home wifi (Ubuntu 12.10)"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by texastwister on 2013-06-02
Sometime in the past week, my system stopped connecting to my primary home wifi ("reconciled" in the output below) secured with WPA-2 Personal.

No changes had been made to the router. I've rebooted the router. Other systems (Ubuntu laptops, Google TV, Android devices) continue connecting to my primary home wifi w/o problem.

No changes had been made to my wireless configuration. 

I *might* have installed some routine system updates, but I can't say for certain. We did have a thunderstorm-related power outage but I can't say whether it coincided with the beginning of this problem.

I can still connect to my unsecured "guest" network. I can still connect to other secured networks (using WPA-2 Personal and WPA-2 Enterprise).

I've deleted and recreated the configuration for that network. I've double-checked that I'm using the same password as the systems that ARE connecting.

I've installed and attempted to use WICD and WIFE Radar, with no success.

What on earth might I be missing? This just seems bizarre...

Output of: $ nm-tool

```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [purcell_guest] -----------------------------------------------
 Type:              802.11 WiFi
 Driver:            iwlwifi
 State:             connected
 Default:           yes
 HW Address:        84:3A:4B:78:F1:E4

 Capabilities:
   Speed:           130 Mb/s

 Wireless Properties
   WEP Encryption:  yes
   WPA Encryption:  yes
   WPA2 Encryption: yes

 Wireless Access Points (* = current AP)
   cuttinupwax:     Infra, 00:13:10:E4:21:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
   westell3596:     Infra, 74:44:01:AE:88:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
   reconciled:      Infra, 1C:AF:F7:D4:59:99, Freq 2422 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
   *purcell_guest:  Infra, 02:AF:F7:D4:59:99, Freq 2422 MHz, Rate 54 Mb/s, Strength 75
   #1houseondablock:Infra, 00:21:2F:37:AA:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
   CBA Hutto ALT:   Infra, C2:9F:DB:1B:66:96, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2

 IPv4 Settings:
   Address:         192.168.0.121
   Prefix:          24 (255.255.255.0)
   Gateway:         192.168.0.1

   DNS:             192.168.0.109
   DNS:             8.8.8.8


- Device: eth0 -----------------------------------------------------------------
 Type:              Wired
 Driver:            e1000e
 State:             unavailable
 Default:           no
 HW Address:        B8:CA:3A:DA:25:C8

 Capabilities:
   Carrier Detect:  yes

 Wired Properties
   Carrier:         off


```

Output of: $ iwlist wlan0 scan

```

wlan0 Scan completed :
Cell 01 - Address: 1C:AF:F74:59:99
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=66/70 Signal level=-44 dBm 
Encryption keyn
ESSID:"reconciled"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001b2a631d3
Extra: Last beacon: 36ms ago
IE: Unknown: 000A7265636F6E63696C6564
IE: Unknown: 010882848B960C121824
IE: Unknown: 030103
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3403001B00000000000000000000000000000000000000
IE: Unknown: 3D1603001B00000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000004000
IE: Unknown: DD770050F204104A0001101044000102103B00010310470010000000000000100000001CAFF7D4599910210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103
Cell 02 - Address: 02:AF:F74:59:99
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=65/70 Signal level=-45 dBm 
Encryption keyff
ESSID:"purcell_guest"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001b2a64a67
Extra: Last beacon: 36ms ago
IE: Unknown: 000D70757263656C6C5F6775657374
IE: Unknown: 010882848B960C121824
IE: Unknown: 030103
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3403001B00000000000000000000000000000000000000
IE: Unknown: 3D1603001B00000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000004000
Cell 03 - Address: 00:13:10:E4:21:B4
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=38/70 Signal level=-72 dBm 
Encryption keyn
ESSID:"cuttinupwax"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000a390882813
Extra: Last beacon: 3068ms ago
IE: Unknown: 000B63757474696E7570776178
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: DD06001018020100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 04 - Address: 00:0D:B9:22:55:8C
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=20/70 Signal level=-90 dBm 
Encryption keyn
ESSID:"local"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000c34b50a84
Extra: Last beacon: 27480ms ago
IE: Unknown: 00056C6F63616C
IE: Unknown: 010882848B960C121824
IE: Unknown: 030102
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD2A000C42000000011E0400000000661E030000526164696F20310000000000000000000000000005027109
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 05 - Address: 74:44:01:AE:88:C4
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=24/70 Signal level=-86 dBm 
Encryption keyn
ESSID:"westell3596"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000b537e1e185
Extra: Last beacon: 6576ms ago
IE: Unknown: 000B77657374656C6C33353936
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: Unknown: 32040C121860
IE: Unknown: DD090010180203F0040000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 06 - Address: 00:21:2F:37:AA:F2
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=22/70 Signal level=-88 dBm 
Encryption keyn
ESSID:"#1houseondablock"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000283332ea00
Extra: Last beacon: 6588ms ago
IE: Unknown: 00102331686F7573656F6E6461626C6F636B
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 050400030000
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1606050000000000000000000000000000000000000000
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3406050000000000000000000000000000000000000000
IE: Unknown: DD0700E04C02022000
IE: Unknown: DD0E0050F204104A0001101044000102
Cell 07 - Address: 68:7F:74:72:8E:36
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=17/70 Signal level=-93 dBm 
Encryption keyn
ESSID:"CETECH0095793L_Network"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000141acbb180
Extra: Last beacon: 16988ms ago
IE: Unknown: 0016434554454348303039353739334C5F4E6574776F726B
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
IE: Unknown: 3D1606001B00000000000000000000000000000000000000
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000000000
IE: Unknown: DD0E0050F204104A0001101044000102

```

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by texastwister on 2013-06-02
And, here's output from syslog as I try to connect:

```
Jun  2 18:43:28 scott-Latitude-E6530 scott: Mark start of attempt to connect to reconciled
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) starting connection 'reconciled'
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0/wireless): connection 'reconciled' has security, and secrets exist.  No new secrets needed.
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'ssid' value 'reconciled'
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'scan_ssid' value '1'
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'psk' value '<omitted>'
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  2 18:43:39 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: set interface ap_scan to 1
Jun  2 18:43:39 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Failed to initiate AP scan
Jun  2 18:43:39 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:40 scott-Latitude-E6530 kernel: [  309.092226] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:40 scott-Latitude-E6530 kernel: [  309.094712] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:40 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:40 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> associating
Jun  2 18:43:40 scott-Latitude-E6530 kernel: [  309.096490] wlan0: authenticated
Jun  2 18:43:40 scott-Latitude-E6530 kernel: [  309.096701] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:40 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:40 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:43:43 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:43 scott-Latitude-E6530 kernel: [  312.612873] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:43 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:43 scott-Latitude-E6530 kernel: [  312.614525] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:43 scott-Latitude-E6530 kernel: [  312.616318] wlan0: authenticated
Jun  2 18:43:43 scott-Latitude-E6530 kernel: [  312.616532] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:43 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> associating
Jun  2 18:43:43 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:43 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:43:47 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:47 scott-Latitude-E6530 kernel: [  316.090631] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:47 scott-Latitude-E6530 kernel: [  316.093360] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:47 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:47 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:43:47 scott-Latitude-E6530 kernel: [  316.095250] wlan0: authenticated
Jun  2 18:43:47 scott-Latitude-E6530 kernel: [  316.095449] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:47 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:43:47 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:47 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:43:50 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:50 scott-Latitude-E6530 kernel: [  319.562329] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:50 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:50 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:43:50 scott-Latitude-E6530 kernel: [  319.564741] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:50 scott-Latitude-E6530 kernel: [  319.566490] wlan0: authenticated
Jun  2 18:43:50 scott-Latitude-E6530 kernel: [  319.566816] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:50 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:43:50 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:50 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:43:53 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:53 scott-Latitude-E6530 kernel: [  323.078433] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:53 scott-Latitude-E6530 kernel: [  323.080091] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:54 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:54 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> associating
Jun  2 18:43:54 scott-Latitude-E6530 kernel: [  323.081936] wlan0: authenticated
Jun  2 18:43:54 scott-Latitude-E6530 kernel: [  323.082181] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:54 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:54 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:43:57 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:57 scott-Latitude-E6530 kernel: [  326.596366] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:43:57 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:43:57 scott-Latitude-E6530 kernel: [  326.599037] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:43:57 scott-Latitude-E6530 kernel: [  326.600842] wlan0: authenticated
Jun  2 18:43:57 scott-Latitude-E6530 kernel: [  326.601225] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:43:57 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:43:57 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:43:57 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:43:57 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:01 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:01 scott-Latitude-E6530 kernel: [  330.110476] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:01 scott-Latitude-E6530 kernel: [  330.112962] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:01 scott-Latitude-E6530 kernel: [  330.114733] wlan0: authenticated
Jun  2 18:44:01 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:01 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> associating
Jun  2 18:44:01 scott-Latitude-E6530 kernel: [  330.115075] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:01 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:01 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:04 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:04 scott-Latitude-E6530 kernel: [  333.629962] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:04 scott-Latitude-E6530 kernel: [  333.632597] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:04 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:04 scott-Latitude-E6530 kernel: [  333.636707] wlan0: authenticated
Jun  2 18:44:04 scott-Latitude-E6530 kernel: [  333.636967] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <warn> Activation (wlan0/wireless): association took too long.
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jun  2 18:44:04 scott-Latitude-E6530 NetworkManager[1197]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0/wireless): connection 'reconciled' has security, and secrets exist.  No new secrets needed.
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'ssid' value 'reconciled'
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'scan_ssid' value '1'
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: added 'psk' value '<omitted>'
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  2 18:44:07 scott-Latitude-E6530 NetworkManager[1197]: <info> Config: set interface ap_scan to 1
Jun  2 18:44:07 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Failed to initiate AP scan
Jun  2 18:44:08 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:08 scott-Latitude-E6530 kernel: [  337.125451] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:08 scott-Latitude-E6530 kernel: [  337.127973] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:08 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:08 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> associating
Jun  2 18:44:08 scott-Latitude-E6530 kernel: [  337.129751] wlan0: authenticated
Jun  2 18:44:08 scott-Latitude-E6530 kernel: [  337.130103] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:08 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:08 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:11 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:11 scott-Latitude-E6530 kernel: [  340.643467] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:11 scott-Latitude-E6530 kernel: [  340.645911] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:11 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:11 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:11 scott-Latitude-E6530 kernel: [  340.648078] wlan0: authenticated
Jun  2 18:44:11 scott-Latitude-E6530 kernel: [  340.648507] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:11 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:11 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:11 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:15 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:15 scott-Latitude-E6530 kernel: [  344.110143] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:15 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:15 scott-Latitude-E6530 kernel: [  344.112900] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:15 scott-Latitude-E6530 kernel: [  344.114706] wlan0: authenticated
Jun  2 18:44:15 scott-Latitude-E6530 kernel: [  344.115078] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:15 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:15 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:15 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:15 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:18 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:18 scott-Latitude-E6530 kernel: [  347.525402] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:18 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:18 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:18 scott-Latitude-E6530 kernel: [  347.530675] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:18 scott-Latitude-E6530 kernel: [  347.532468] wlan0: authenticated
Jun  2 18:44:18 scott-Latitude-E6530 kernel: [  347.532743] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:18 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:18 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:18 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:21 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:21 scott-Latitude-E6530 kernel: [  351.048984] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:21 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:21 scott-Latitude-E6530 kernel: [  351.051661] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:21 scott-Latitude-E6530 kernel: [  351.053452] wlan0: authenticated
Jun  2 18:44:21 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:21 scott-Latitude-E6530 kernel: [  351.053904] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:22 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:22 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:22 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:25 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:25 scott-Latitude-E6530 kernel: [  354.571370] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:25 scott-Latitude-E6530 kernel: [  354.574159] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:25 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:25 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:25 scott-Latitude-E6530 kernel: [  354.575974] wlan0: authenticated
Jun  2 18:44:25 scott-Latitude-E6530 kernel: [  354.576232] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:25 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:25 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:25 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:29 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:29 scott-Latitude-E6530 kernel: [  358.113885] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:29 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:29 scott-Latitude-E6530 kernel: [  358.116698] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:29 scott-Latitude-E6530 kernel: [  358.118545] wlan0: authenticated
Jun  2 18:44:29 scott-Latitude-E6530 kernel: [  358.119120] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:29 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:29 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:29 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:29 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:32 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: SME: Trying to authenticate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:32 scott-Latitude-E6530 kernel: [  361.606615] wlan0: authenticate with 1c:af:f7:d4:59:99
Jun  2 18:44:32 scott-Latitude-E6530 wpa_supplicant[3819]: wlan0: Trying to associate with 1c:af:f7:d4:59:99 (SSID='reconciled' freq=2422 MHz)
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun  2 18:44:32 scott-Latitude-E6530 kernel: [  361.609199] wlan0: send auth to 1c:af:f7:d4:59:99 (try 1/3)
Jun  2 18:44:32 scott-Latitude-E6530 kernel: [  361.611040] wlan0: authenticated
Jun  2 18:44:32 scott-Latitude-E6530 kernel: [  361.611374] wlan0: waiting for beacon from 1c:af:f7:d4:59:99
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <warn> Activation (wlan0/wireless): association took too long.
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jun  2 18:44:32 scott-Latitude-E6530 NetworkManager[1197]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  2 18:44:47 scott-Latitude-E6530 scott: Mark end of attempt to connect to reconciled
```

---

### Post by texastwister on 2013-06-02
Switching to WPA2 only appears to have resolved it.  Thanks for the suggestions!

---

### Post by setheb on 2013-06-02
I know how it can get with kernel upgrades, module differences/configurations and keeping track of hardware modes and device names when you're messing around with wifi adapters. Meh.

My gut is telling me the router is to blame. I say that because it's definitely a configuration issue, and the router is more time consuming to configure, so don't be shy.

So let's quickly make things all nice and neat here by separating what you've got going. Never mind the specifics of the other APs at this point. Focus on the differences between yours.

This is the output for your secured network:> **texastwister said:**
> ```
Cell 01 - Address: 1C:AF:F74:59:99
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=66/70 Signal level=-44 dBm 
Encryption keyn
ESSID:"reconciled"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001b2a631d3
Extra: Last beacon: 36ms ago
IE: Unknown: 000A7265636F6E63696C6564
IE: Unknown: 010882848B960C121824
IE: Unknown: 030103
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3403001B00000000000000000000000000000000000000
IE: Unknown: 3D1603001B00000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000004000
IE: Unknown: DD770050F204104A0001101044000102103B00010310470010000000000000100000001CAFF7D4599910210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103
```
And this is the output from your unsecured guest network:> **texastwister said:**
> ```
Cell 02 - Address: 02:AF:F74:59:99
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=65/70 Signal level=-45 dBm 
Encryption keyff
ESSID:"purcell_guest"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001b2a64a67
Extra: Last beacon: 36ms ago
IE: Unknown: 000D70757263656C6C5F6775657374
IE: Unknown: 010882848B960C121824
IE: Unknown: 030103
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3403001B00000000000000000000000000000000000000
IE: Unknown: 3D1603001B00000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000004000
```I'll assume the MAC addresses are fine. :) They're different.

Because the other 4 APs are operating on CH 6 (2.437 MHz), I will infer they are using a 20 MHz channel width to support 802.11b and/or 802.11g/n modes. Same goes for the additional AP on CH 2 (2.417 MHz).

You, however, are operating your APs on CH 3. You're in a [prime spot]("http://upload.wikimedia.org/wikipedia/commons/8/84/NonOverlappingChannels2.4GHzWLAN-en.svg") to operate in 802.11n mode within a 40MHz channel width just as is CH 11. (It's actually 2x20 MHz streams). But from CH 3 the additional 20 MHz must be extended into the upper part of the 2.4 GHz band (HT40+) just as CH 11 must extend its extra 20 MHz into the lower part (HT40-) in order to be operate within the 2.4 GHz - 2.4835 GHz wireless range. (Actually I think the "channel" becomes the middle of its range, and the streams can dynamically allocated, but this is the configuration-oriented way of putting it.)

So, there's a width selector to think about. Then an upper/lower flag to deal with. Then there's the fact that you can only use WPA2 with AES encryption in that configuration. Then there's the fact that regulatory requirements have the driver scanning for other BSSIDs your 40 MHz block is overlapping... which includes CH 2 and CH 6. As far as your configuration is concerned, it's best to skip that kind of scanning.

I think another good place to look is for configuration problems with your guest network, perhaps within the firewall. I recommend you flash the firmware of your router to its latest, reset everything to defaults and start with nice-and-easy configurations until you work yourself up into faster speeds.

Edit: Oh, man, you fixed it while I was typing this monstrous thing... :-(

Good going!

---

