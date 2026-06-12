---
title: "WPA not connecting in 9.04"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by rvgsd on 2009-05-07
Hi All, 
I have recently installed Ubuntu 9.04, and am a relatively new user.
I have BCM4306 with the drivers auto-installed by ubuntu using b43-fwcutter.

I am able to connect to the Unsecured Networks but not my secured Network which is Wpa2. This makes my Ubuntu pretty much Unusable and I have to stick to Windows :(. Any help is appreciated. I would be glad to switch to Ubuntu permanently :) 

I Opened "/etc/network/interfaces":

```
auto lo
iface lo inet loopback
```

After going through this topic: 
[http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x)
I modified it as follows:

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MYESSID
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk MY_HEX_KEY

```

so when I run **'sudo /etc/init.d/networking restart'**
here's what I get: 
```

* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 4764
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   LPF/wlan0/00:90:4b:2d:e7:e2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Heres the result of **'sudo iwlist scan'**:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:46:C8:80
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000d62a2db09
                    Extra: Last beacon: 1484ms ago
          Cell 02 - Address: 00:18:3A:AF:2D:B2
                    ESSID:"NITTIANS@TAMU"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 000D4E49545449414E534054414D55
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000014e9a0b5170
                    Extra: Last beacon: 1140ms ago
          Cell 03 - Address: 00:18:3A:D6:EF:54
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/100  Signal level:-63 dBm  Noise level=-55 dBm
                    Encryption key:off
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002496f4a184
                    Extra: Last beacon: 920ms ago
          Cell 04 - Address: 00:1C:10:46:00:30
                    ESSID:"Horizon"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 0007486F72697A6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000af472b43d7
                    Extra: Last beacon: 1144ms ago
          Cell 05 - Address: 00:14:D1:30:BF:14
                    ESSID:"carmen"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level:-79 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 00066361726D656E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000229011f5181
                    Extra: Last beacon: 1164ms ago
          Cell 06 - Address: 00:12:0E:8A:B1:CE
                    ESSID:"07FX09079070"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level:-77 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 000C303746583039303739303730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000fc17f238
                    Extra: Last beacon: 1292ms ago
          Cell 07 - Address: 00:1C:DF:3F:24:09
                    ESSID:"MYNETWORK"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=83/100  Signal level:-49 dBm  Noise level=-55 dBm
                    Encryption key:on
                    IE: Unknown: 00124C6F7374496E476F6C664279506C75733131
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000ea24d2181
                    Extra: Last beacon: 32ms ago
```

---

### Post by rvgsd on 2009-05-11
(Bump!) Any help at all on this one???

---

