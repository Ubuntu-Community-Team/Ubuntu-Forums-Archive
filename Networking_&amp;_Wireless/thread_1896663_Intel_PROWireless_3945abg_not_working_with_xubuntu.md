---
title: "Intel PRO/Wireless 3945abg not working with xubuntu 11.10"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by river6 on 2011-12-17
```

uname -r 

3.0.0-12-generic

lspci | grep 3945

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

lsmod | grep iwl

iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

iwlist scan 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:8B:AA:43
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"newkentnlcf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000097e95bfc6
                    Extra: Last beacon: 7148ms ago
                    IE: Unknown: 000B6E65776B656E746E6C6366
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010200
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:21:29:6E:AD:6F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:off
                    ESSID:"732"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ab3ba64c4
                    Extra: Last beacon: 7092ms ago
                    IE: Unknown: 0003373332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000101103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483445323632381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180200F4000000
          Cell 03 - Address: 00:22:6B:5B:4C:E8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Placebo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c47b99baba
                    Extra: Last beacon: 7288ms ago
                    IE: Unknown: 0007506C616365626F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 68:7F:74:FE:2F:0E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"potatoes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000044bfb580b
                    Extra: Last beacon: 7076ms ago
                    IE: Unknown: 0008706F7461746F6573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F74FE2F0E102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B4244373935371054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:23:69:CC:0F:CF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"NKR407"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b6e8fb82
                    Extra: Last beacon: 7372ms ago
                    IE: Unknown: 00064E4B52343037
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3549363838381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 94:44:52:96:30:31
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Belkin.3031"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004af2fe5184
                    Extra: Last beacon: 7736ms ago
                    IE: Unknown: 000B42656C6B696E2E33303331
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0400000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B00010310470010000000000000000110009444529630311021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323130323647313130323933391054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
          Cell 07 - Address: C0:3F:0E:66:A8:64
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dc0d8a190
                    Extra: Last beacon: 6832ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700100EAFDF0EE0D7AE0C872ED4B354DB21C01021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 06:24:36:AD:8F:2F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Persephone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b0dac0d55
                    Extra: Last beacon: 8320ms ago
                    IE: Unknown: 000A506572736570686F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0208
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106002436AD8F30
          Cell 09 - Address: 00:26:F2:94:3C:5C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"NESS-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000166e48d80
                    Extra: Last beacon: 8252ms ago
                    IE: Unknown: 000F4E4553532D50435F4E6574776F726B
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000000026F2943C5C103C000103
          Cell 10 - Address: 00:26:F3:FF:F3:1B
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000055d84cece4
                    Extra: Last beacon: 8036ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1603050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000018127A
                    IE: Unknown: DD07000C4300000000
          Cell 11 - Address: 0C:D5:02:81:9E:66
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"KandH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000374b6252183
                    Extra: Last beacon: 6980ms ago
                    IE: Unknown: 00054B616E6448
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
          Cell 12 - Address: 00:22:3F:B9:B5:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Sam_****_boy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004c62411183
                    Extra: Last beacon: 6904ms ago
                    IE: Unknown: 000C53616D5F4655434B5F626F79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: C0:3F:0E:09:7A:38
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c492aa18f
                    Extra: Last beacon: 6880ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000


```

I can see APs in my list, but I cannot connect to them. The wifi card worked with an old version of ubuntu. After upgrading to 11.10, it does not work any more. Can someone help me? 

Thanks.

---

### Post by river6 on 2011-12-17
dmesg output

```

[   28.400281] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.516430] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   28.585813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.138151] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   30.138355] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.418956] Bluetooth: Core ver 2.16
[   31.418992] NET: Registered protocol family 31
[   31.418995] Bluetooth: HCI device and connection manager initialized
[   31.418998] Bluetooth: HCI socket layer initialized
[   31.419000] Bluetooth: L2CAP socket layer initialized
[   31.419073] Bluetooth: SCO socket layer initialized
[   31.424384] Bluetooth: RFCOMM TTY layer initialized
[   31.424391] Bluetooth: RFCOMM socket layer initialized
[   31.424393] Bluetooth: RFCOMM ver 1.11
[   31.435249] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.435253] Bluetooth: BNEP filters: protocol multicast
[   34.284586] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   35.705308] wlan0: direct probe to 00:13:10:8c:39:e0 (try 1/3)
[   35.904048] wlan0: direct probe to 00:13:10:8c:39:e0 (try 2/3)
[   36.104217] wlan0: direct probe to 00:13:10:8c:39:e0 (try 3/3)
[   36.242519] init: plymouth-stop pre-start process (1235) terminated with status 1
[   36.304070] wlan0: direct probe to 00:13:10:8c:39:e0 timed out
[   39.978605] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   40.408035] eth0: no IPv6 routers present
[   43.684676] wlan0: authenticate with 00:13:10:8c:39:e0 (try 1)
[   43.686587] wlan0: authenticated
[   43.690100] wlan0: associate with 00:13:10:8c:39:e0 (try 1)
[   43.700485] wlan0: RX AssocResp from 00:13:10:8c:39:e0 (capab=0x401 status=0 aid=5)
[   43.700490] wlan0: associated
[   43.702929] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.672032] wlan0: no IPv6 routers present
[   64.431531] iwl3945 0000:06:00.0: Card state received: HW:Kill SW:On
[   64.431783] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.431788] iwl3945 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[   64.431799] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.431803] iwl3945 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[   64.431806] iwl3945 0000:06:00.0: Error setting RXON_ASSOC configuration (-5).
[   64.431811] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.431814] iwl3945 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[   64.431817] iwl3945 0000:06:00.0: Error setting new configuration (-5).
[   64.431820] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.431823] iwl3945 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[   64.431827] wlan0: deauthenticating from 00:13:10:8c:39:e0 by local choice (reason=3)
[   64.431867] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.431871] iwl3945 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[   64.431874] iwl3945 0000:06:00.0: Error removing station 00:13:10:8c:39:e0
[   64.444187] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.444198] iwl3945 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[   64.444211] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.444218] iwl3945 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[   64.444231] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.444238] iwl3945 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[   64.444245] iwl3945 0000:06:00.0: Error setting new configuration (-5).
[   64.444281] cfg80211: All devices are disconnected, going to restore regulatory settings
[   64.444300] cfg80211: Restoring regulatory settings
[   64.444326] cfg80211: Calling CRDA to update world regulatory domain
[   64.449278] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   64.449282] cfg80211: World regulatory domain updated:
[   64.449284] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   64.449288] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.449292] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   64.449296] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   64.449299] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.449303] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.460112] iwl3945 0000:06:00.0: Not sending command - RF KILL
[   64.460124] iwl3945 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[   64.460133] iwl3945 0000:06:00.0: Error setting new configuration (-5).
[   64.464018] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD

```

---

### Post by Toz on 2011-12-17
Try:
```
sudo rfkill list
```

If wlan0 is soft blocked, then:
```
sudo rfkill unblock wlan0
```

If wlan0 is hard blocked, then look for hardware switch than may be set to off position or off/disabled in bios.

---

### Post by river6 on 2011-12-18
Thanks. It is already fixed somehow. I do not know how, but it is working now.

---

