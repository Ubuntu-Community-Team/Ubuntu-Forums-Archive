---
title: "Wireless won't connect"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by staffann on 2010-07-29
I just upgraded to 10.04LTS and I'm having more of the same problem that I had on the previous release - I cannot connect to my wireless network. I used to be able to by waiting, restarting the network service and fiddling about but now it seems impossible.

I have a Philips SNU5600 wireless adapter that connects to an USB port. I have installed it using ndiswrapper and the windows drivers.

The networking interface file looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan2
iface wlan2 inet static
    address 192.168.1.4
    gateway 192.168.1.2
    netmask 255.255.255.0
    wpa-driver wext
    wpa-ssid staffan
    wpa-ap-scan 1
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk ***my converted passkey **

```If I try iwconfig it says:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```iwlist scanning shows one, two or sometimes three other networks, but not mine:
```

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: 00:23:54:89:F5:09
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level=31/100
                    Encryption key:on
                    ESSID:"630273"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000918f36505c
                    Extra: Last beacon: 2684ms ago
                    IE: Unknown: 0006363330323733
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD6A0050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0EBB10210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006363330323733100800020088
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:24:8C:8A:D6:AF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/100  Signal level=10/100
                    Encryption key:off
                    ESSID:"skogen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001861748005
                    Extra: Last beacon: 8316ms ago
                    IE: Unknown: 0006736B6F67656E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:22:15:28:3C:12
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/100  Signal level=7/100
                    Encryption key:on
                    ESSID:"F&O"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002c394364a49
                    Extra: Last beacon: 13808ms ago
                    IE: Unknown: 000346264F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0EBB102100075765625354415210230007576562535441521024000631323334353610420007303030303030311054000800060050F204000110110009576562535441524150100800020088
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:18:4D:97:86:9A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=9/100  Signal level=9/100
                    Encryption key:on
                    ESSID:"PARIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001a42ba555f5e
                    Extra: Last beacon: 7968ms ago
                    IE: Unknown: 00055041524953
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```lsusb finds my wireless adaptor:
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0471:1236 Philips SNU5600 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```What should I do to find the problem and correct it?

---

