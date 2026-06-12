---
title: "Can not switch between school wireless"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by digforbear on 2013-07-18
I'm running Ubuntu 12.04 on an Acer A0756.  I am a graduate student at a large school and we have many wireless networks.  When the computer first boots it automatically connects to "UB Wireless" and then I must open firefox and type in my email and password to access the internet.  If I try to switch to a different network "UB Guest" for example it disconnects me from "UB Wireless" and then after that I can no longer connect to any network including reconnecting to "UB Wireless."  I have to restart my computer to get back on the internet.  Any help or insight into what is going wrong is very much appecriated!

Hopefully this information is useful:
```
michael@little-guy:~$ sudo iwlist eth1 scan
[sudo] password for michael: 
eth1      Scan completed :
          Cell 01 - Address: E8:40:40:DE:0B:80
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000B55425F576972656C657373
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100048D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF8D09018093F0100008903000000009C222F125E73B7B9
          Cell 02 - Address: E8:40:40:DE:0B:81
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"UB_Secure"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000955425F536563757265
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100058D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C03EAF8FB9118093F010000FD680F00000016BF63A4CB2667C0
          Cell 03 - Address: E8:40:40:DE:0B:83
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000855425F4775657374
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100068D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF035900776C732D6D617468312D3135300000000100003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF8C39118093F010000E6670F0000003F18C7BFED7FFF2C
          Cell 04 - Address: E8:40:40:DE:0B:84
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000955425F47616D696E67
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100058D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF035900776C732D6D617468312D3135300000000100003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF81F9218093F010000FB680F000000D223D3627E6E6648
          Cell 05 - Address: E8:40:40:DE:0B:82
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"UB_Voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000855425F566F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100058D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C03EAF8139218093F010000FC680F000000D5E3544E346B6786
          Cell 06 - Address: E8:40:40:DE:76:D0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000B55425F576972656C657373
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000028D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF80F5C17A13F0100005D1100000000D1B01424BE6F96F4
          Cell 07 - Address: E8:40:40:DE:76:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000955425F47616D696E67
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000038D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF035900776C732D6D617468312D3135320000000000003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF8C55D17A13F010000065F0F0000000E652330165C8A22
          Cell 08 - Address: E8:40:40:DE:76:D2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UB_Voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000855425F566F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000038D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C03EAF8B85D17A13F010000075F0F000000FDDE33387FD9147C
          Cell 09 - Address: E8:40:40:DE:76:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UB_Secure"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000955425F536563757265
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000038D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C03EAF8A05D17A13F010000085F0F00000037C873B2116211DA
          Cell 10 - Address: E8:40:40:DE:76:D3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000855425F4775657374
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000038D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 851E03008F000F00FF035900776C732D6D617468312D3135320000000000003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF8685D17A13F010000A211000000006671C697D6389C77
          Cell 11 - Address: E8:40:40:DE:85:74
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000955425F47616D696E67
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050100028D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 851E02008F000F00FF035900776C732D6D617468312D3135340000000100003A
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
                    IE: Unknown: DD1D0040960C03EAF83EE347F03F010000026B0F0000000A6AFE98A35E73B0

michael@little-guy:~$ 


```

```
michael@little-guy:~$ sudo tail -f /var/log/syslog
Jul 18 10:22:13 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:76:d3 (SSID='UB_Guest' freq=2462 MHz)
Jul 18 10:22:13 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:13 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:18 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:76:d3 timed out.
Jul 18 10:22:18 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:18 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:83 (SSID='UB_Guest' freq=2437 MHz)
Jul 18 10:22:18 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:18 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:23 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:83 timed out.
Jul 18 10:22:24 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:25 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:83 (SSID='UB_Guest' freq=2437 MHz)
Jul 18 10:22:25 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:25 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:27 little-guy NetworkManager[769]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Jul 18 10:22:27 little-guy NetworkManager[769]: <info> (eth1): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jul 18 10:22:27 little-guy NetworkManager[769]: <warn> Activation (eth1) failed for access point (UB_Guest)
Jul 18 10:22:27 little-guy NetworkManager[769]: <warn> Activation (eth1) failed.
Jul 18 10:22:27 little-guy NetworkManager[769]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jul 18 10:22:27 little-guy NetworkManager[769]: <info> (eth1): deactivating device (reason 'none') [0]
Jul 18 10:22:27 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> disconnected
Jul 18 10:22:27 little-guy NetworkManager[769]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Auto-activating connection 'UB_Wireless'.
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) starting connection 'UB_Wireless'
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1/wireless): connection 'UB_Wireless' requires no security.  No secrets needed.
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Config: added 'ssid' value 'UB_Wireless'
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Config: added 'scan_ssid' value '1'
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Config: added 'key_mgmt' value 'NONE'
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> Config: set interface ap_scan to 1
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jul 18 10:22:30 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:80 (SSID='UB_Wireless' freq=2437 MHz)
Jul 18 10:22:30 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:30 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:35 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:80 timed out.
Jul 18 10:22:36 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:38 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:80 (SSID='UB_Wireless' freq=2437 MHz)
Jul 18 10:22:38 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:38 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:43 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:80 timed out.
Jul 18 10:22:43 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:43 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:76:d0 (SSID='UB_Wireless' freq=2462 MHz)
Jul 18 10:22:43 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:43 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:48 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:76:d0 timed out.
Jul 18 10:22:48 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:50 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:76:d0 (SSID='UB_Wireless' freq=2462 MHz)
Jul 18 10:22:50 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:50 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:22:55 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:76:d0 timed out.
Jul 18 10:22:55 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:22:56 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:80 (SSID='UB_Wireless' freq=2437 MHz)
Jul 18 10:22:56 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:22:56 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:23:01 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:80 timed out.
Jul 18 10:23:01 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:23:03 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:80 (SSID='UB_Wireless' freq=2437 MHz)
Jul 18 10:23:03 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:23:03 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:23:08 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:80 timed out.
Jul 18 10:23:08 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:23:09 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:76:d0 (SSID='UB_Wireless' freq=2462 MHz)
Jul 18 10:23:09 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:23:09 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): disconnecting for new activation request.
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): device state change: config -> disconnected (reason 'none') [50 30 0]
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): deactivating device (reason 'none') [0]
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) starting connection 'UB_Guest'
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1/wireless): connection 'UB_Guest' requires no security.  No secrets needed.
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Config: added 'ssid' value 'UB_Guest'
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Config: added 'scan_ssid' value '1'
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Config: added 'key_mgmt' value 'NONE'
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> disconnected
Jul 18 10:23:13 little-guy NetworkManager[769]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 18 10:23:13 little-guy NetworkManager[769]: <info> Config: set interface ap_scan to 1
Jul 18 10:23:14 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: disconnected -> scanning
Jul 18 10:23:15 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:83 (SSID='UB_Guest' freq=2437 MHz)
Jul 18 10:23:15 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:23:15 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
Jul 18 10:23:20 little-guy wpa_supplicant[847]: Authentication with e8:40:40:de:0b:83 timed out.
Jul 18 10:23:21 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: associating -> scanning
Jul 18 10:23:21 little-guy wpa_supplicant[847]: Trying to associate with e8:40:40:de:0b:83 (SSID='UB_Guest' freq=2437 MHz)
Jul 18 10:23:21 little-guy wpa_supplicant[847]: Association request to the driver failed
Jul 18 10:23:21 little-guy NetworkManager[769]: <info> (eth1): supplicant interface state: scanning -> associating
^Z
[1]+  Stopped                 sudo tail -f /var/log/syslog
michael@little-guy:~$ 


```

---

### Post by praseodym on 2013-07-18
Hi,

what hardware is in use?
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
```

---

### Post by digforbear on 2013-07-18
thanks for the response!

```
michael@little-guy:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0742]
    Kernel driver in use: tg3
--
04:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0742]
    Kernel driver in use: sdhci-pci
```

```
michael@little-guy:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:d251 Suyin Corp. 

```

```
michael@little-guy:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17275  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2906597  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
psmouse                86520  0 
serio_raw              13027  0 
videodev               86588  1 uvcvideo
cfg80211              178877  1 wl
i915                  428056  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
video                  19115  1 i915
wmi                    18744  1 acer_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141414  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
```

```
michael@little-guy:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"UB_Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:40:40:DE:0B:80   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

```
michael@little-guy:~$ iwlist chan
lo        no frequency information.

eth1      32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency=2.437 GHz (Channel 6)

eth0      no frequency information.
```

---

### Post by praseodym on 2013-07-18
Try to add this software-switch (from [http://forum.ubuntuusers.de/topic/2-x-wlan-im-haushalt-immer-mit-dem-staerksten-sign/?highlight=skript+wlan+libnotify#post-3440377](http://forum.ubuntuusers.de/topic/2-x-wlan-im-haushalt-immer-mit-dem-staerksten-sign/?highlight=skript+wlan+libnotify#post-3440377) )

```
sudo apt-get install libnotify-bin gnome-netstatus-applet 
```
Create the file:```

touch wlan_ap_switch.sh
chmod +x wlan_ap_switch.sh 
```
Add the content of the 1st grey box, but insert the appropriate content for your school access points. Check the outputs of "sudo iwlist scan" for CCMP, MAC-addresses, etc., and add these information appropriately. ("das_Kennwort_in_Klartext" means "non-encrypted password"

Second script 1-to-1 with the 2nd grey box. Move the files to /usr/sbin.

Create a starter which uses the command line
```
gksu /usr/sbin/wlan_ap_switch_control.sh 
```

---

### Post by digforbear on 2013-07-18
Thanks again for the help. It is a bit over my head, and I don't read German, but I'll give it a try.  One thing I noticed is that in the first and second script should I change wlan0 to eth1?

```
wlaniface="wlan0"
```

to

```
wlaniface="eth1"
```
?

---

### Post by praseodym on 2013-07-18
Yes. Please check for

non-encrypted networks "UB_Wireless" "UB_Guest" "UB_Gaming" the entries should not be necessary.

For mixed WPA/WPA2-encryption ("UB_Voice") it should look like

[http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA-Verschluesselung](http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA-Verschluesselung)

For WPA2 "UB_Secure"

[http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung](http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung)

The MAC-addresses and encryption modes are shown like this:```


          Cell 08 - Address: [COLOR="#FF0000"]E8:40:40:DE:76:D2[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:[COLOR="#FF0000"]on[/COLOR]
                    ESSID:"UB_Voice"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000855425F566F696365
                    IE: Unknown: 01069824B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050000038D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="#FF0000"]CCMP[/COLOR]
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 9606004096001400
                    IE: [COLOR="#FF0000"]WPA Version 1[/COLOR]
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="#FF0000"]TKIP[/COLOR]
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
                    IE: Unknown: DD1D0040960C03EAF8B85D17A13F010000075F0F000000FDDE33387FD9147C
```

Similar for WPA2

---

### Post by praseodym on 2013-07-19
[ATTACH]244863[/ATTACH]
[ATTACH]244864[/ATTACH]

Please find the first file attached for your 10 APs. I do not know if it works with unsecure networks, if the variables are "clear", just give it a try.

Save both files in "Downloads" and install:
```

sudo apt-get install libnotify-bin gnome-netstatus-applet
cd ~/Downloads/
chmod +x wlan_ap_switch.sh 
chmod +x wlan_ap_switch_control.sh 
sudo cp wlan_ap_switch_control.sh /usr/sbin
sudo cp wlan_ap_switch.sh /usr/sbin 
```
Create a starter which starts with
```
gksu /usr/sbin/wlan_ap_switch_control.sh 
```

---

