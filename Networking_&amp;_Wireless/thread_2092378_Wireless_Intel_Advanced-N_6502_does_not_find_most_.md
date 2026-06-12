---
title: "Wireless Intel Advanced-N 6502 does not find most of the SSID"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by vmalep on 2012-12-07
Hi,

I just bought a Lenovo X220T (type: 4298-RD9), but the wireless card does not find most of the SSID. I said most of them, because it does find my android phone when I active the tethering mode. Another strange aspect is that I have the Lenovo T420 with the same wireless card and it works well with the same AP... I had a look at the forums this afternoon and found many issues with this card. I also tried the compat-wireless solution, to o avail. If someone could help me, it would be very appreciated.

Some output (I also have a usb wireless card inserted (and working fine).

lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
```

dmesg | grep iwl
```
[    3.542066] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.542069] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[    3.542233] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    3.542235] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050ac000
[    3.542237] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[    3.542459] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[    3.554681] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    3.555055] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.555064] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.555065] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.555067] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    3.555068] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P enabled
[    3.555070] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.555182] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.555381] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[    3.564746] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[    3.564749] iwlwifi 0000:03:00.0: Device SKU: 0x1F0
[    3.564750] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[    3.564764] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.567254] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.384403] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    4.384592] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    4.670927] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    4.671116] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 6321.753189] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 6321.776998] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[ 6321.777298] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[ 6333.012118] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 6333.015596] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 6333.015951] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 6588.334810] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 6588.334813] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[ 6588.334981] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[ 6588.334987] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050a4000
[ 6588.334991] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[ 6588.335484] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[ 6588.338419] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[ 6588.338952] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 6588.338954] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 6588.338955] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 6588.338956] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 6588.338957] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P enabled
[ 6588.338959] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 6588.339066] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 6588.348570] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 6588.348575] iwlwifi 0000:03:00.0: Device SKU: 0x1F0
[ 6588.348576] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[ 6588.348595] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 6588.348918] ieee80211 phy2: Selected rate control algorithm 'iwl-agn-rs'
[ 6588.358063] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 6588.358256] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 6588.645262] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 6588.645466] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
```

rfkill list all:
```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
6: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
vmalep@x220t:~$ uname -a
Linux x220t 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Best regards,
Pierre

Update: To complement the issue, please find hereunder the result of iwlist wlan1 scan from the Lenovo T420 (I moved down the ESSID # 2 to 9 in order to have first my home wifi, then my android phone, the only one found by the x220t computer):

```
wlan1     Scan completed :
          Cell 01 - Address: 00:23:F8:D9:EC:72
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"WLAN_3B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000194c2936469
                    Extra: Last beacon: 18836ms ago
                    IE: Unknown: 0007574C414E5F3342
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 10 - Address: B0:D0:9C:BE:C8:EB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"AndroidAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000332cc1f
                    Extra: Last beacon: 8044ms ago
                    IE: Unknown: 0009416E64726F69644150
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1103FF00000001000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 38:72:C0:A0:AB:41
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"lak"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ca92258b9
                    Extra: Last beacon: 29796ms ago
                    IE: Unknown: 00036C616B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: 00:19:15:D2:35:99
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"WLAN_Murrish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bcd508a3ec
                    Extra: Last beacon: 21760ms ago
                    IE: Unknown: 000C574C414E5F4D757272697368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA20050F204104A0001101044000102103B0001031047001063041253101920061228001915D235991021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100174F4253455256412054454C45434F4D2C20415734303632100800020086
          Cell 13 - Address: 00:90:D0:DB:2D:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouch7EA9BD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000065f9096683
                    Extra: Last beacon: 21608ms ago
                    IE: Unknown: 00105370656564546F756368374541394244
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 14 - Address: 00:24:D1:29:AA:B3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ROBERTO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000117a16fe183
                    Extra: Last beacon: 21616ms ago
                    IE: Unknown: 0007524F424552544F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
          Cell 15 - Address: 00:24:D2:15:3F:0C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Vodafone3F0B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5897a14ae
                    Extra: Last beacon: 21640ms ago
                    IE: Unknown: 000C566F6461666F6E6533463042
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 1C:C6:3C:A1:00:C3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Orange-00C1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fb64d7706
                    Extra: Last beacon: 29536ms ago
                    IE: Unknown: 000B4F72616E67652D30304331
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C332C001EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD8F0050F204104A00011010440001021041000100103B00010310470010000000000000000300001CC63CA100C21021000B436F72706F726174696F6E1023000B41525637353139525732321024000930302E39352E3030351042000A4A3232353035333231321054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD050009860100
          Cell 17 - Address: 00:1A:2B:48:26:F7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_09"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000078c7a118b
                    Extra: Last beacon: 29548ms ago
                    IE: Unknown: 000A4A415A5A54454C5F3039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
          Cell 18 - Address: 62:C7:14:31:F9:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"vodafoneF9C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aaeafb16c
                    Extra: Last beacon: 29532ms ago
                    IE: Unknown: 000C766F6461666F6E6546394332
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860162C71431F9C0103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 19 - Address: 00:A0:26:7F:2C:9C
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WLAN_2C9C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e948a413a
                    Extra: Last beacon: 21612ms ago
                    IE: Unknown: 0009574C414E5F32433943
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A0267F2C9C103C000101
                    IE: Unknown: 050400010018
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502000A127A
                    IE: Unknown: DD07000C4304000000
          Cell 20 - Address: 64:16:F0:5A:6B:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"lml"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b6a359a43
                    Extra: Last beacon: 21716ms ago
                    IE: Unknown: 00036C6D6C
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010000000000000100000006416F05A6BC01021000648756177656910230006484735353661102400085631303052303031104200064847353536611054000800060050F20400011011000D4855415745492D484735353661100800020084103C000103
          Cell 21 - Address: B4:74:9F:04:20:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Jazztel_80"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000015c60b23a17f
                    Extra: Last beacon: 21696ms ago
                    IE: Unknown: 000A4A617A7A74656C5F3830
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 05040001000E
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 22 - Address: 00:16:38:89:1A:14
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_1E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007069c097188
                    Extra: Last beacon: 21664ms ago
                    IE: Unknown: 0007574C414E5F3145
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010C
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018010200
          Cell 23 - Address: 00:1A:2B:90:A7:73
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WLAN_D56E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008da9d965af
                    Extra: Last beacon: 21656ms ago
                    IE: Unknown: 0009574C414E5F44353645
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160C081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340C081100000000000000000000000000000000000000
          Cell 02 - Address: 64:68:0C:0D:E0:45
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"WLAN_E042"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e5d56665
                    Extra: Last beacon: 21952ms ago
                    IE: Unknown: 0009574C414E5F45303432
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: A0:21:B7:D5:D7:24
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ONOD724"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 29988ms ago
                    IE: Unknown: 00074F4E4F44373234
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010F9F9822B2E5EA3BCD1E33F589E192054102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088103C000101
                    IE: Unknown: DD090010180203F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: A0:21:B7:D8:0E:4F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ONO0E4F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000029ad89db185
                    Extra: Last beacon: 22036ms ago
                    IE: Unknown: 00074F4E4F30453446
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD740050F204104A0001101044000102103B00010310470010DC06DE66A78C2684172CD68F21137B0B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303044100800020088103C000101
                    IE: Unknown: DD090010180200F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: BC:14:01:0B:F3:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ONOF300"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016726891b32
                    Extra: Last beacon: 29972ms ago
                    IE: Unknown: 00074F4E4F46333030
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000016127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
          Cell 06 - Address: E0:91:53:5E:09:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"WLAN_10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008a4a261df
                    Extra: Last beacon: 21992ms ago
                    IE: Unknown: 0007574C414E5F3130
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD050010910400
                    IE: Unknown: 050400010000
          Cell 07 - Address: 40:4A:03:7B:01:0A
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_D9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e39bef75af
                    Extra: Last beacon: 22008ms ago
                    IE: Unknown: 0007574C414E5F4439
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: 64:68:0C:43:F4:4B
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"WLAN_F448"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000045cc57c1c88
                    Extra: Last beacon: 22012ms ago
                    IE: Unknown: 0009574C414E5F46343438
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 8C:0C:A3:27:D5:E8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"WLAN_D5E8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b4b34895a0
                    Extra: Last beacon: 21876ms ago
                    IE: Unknown: 0009574C414E5F44354538
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010088127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7D0050F204104A00011010440001021041000100103B00010310470010C633C70D57950E0DED348C0CA327D5E8102100084D6F7669737461721023000941534C2D32363535351024000941534C2D32363535351042000830303030303030301054000800060050F20400011011000941534C2D3236353535100800020086

```

---

### Post by vmalep on 2012-12-07
Update: I thought I had detected a difference in the output of dmesg | grep iwl between my X220T and my T420 laptops ("iwlwifi 0000:03:00.0: Not sending command - RF KILL"), but after having uninstalled the compat-wireless, the 2 computer gives the same result... So I delete this message.

This is the new output of this command on the X220T (without compat-wireless):
```
[    3.334426] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.334429] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[    3.334563] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    3.334565] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050ac000
[    3.334567] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[    3.336282] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[    3.456397] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    3.456808] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.456811] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.456812] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.456814] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    3.456815] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    3.456817] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.456980] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.467304] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[    3.467307] iwlwifi 0000:03:00.0: Device SKU: 0x1F0
[    3.467309] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[    3.467329] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.470648] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.250348] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    4.250555] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    4.536453] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    4.536645] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
```

---

### Post by vmalep on 2012-12-08
Hi,

Eventually, the problem had nothing to do with Ubuntu. I restored Windows 7 and figures out it had the same issue. I then decided to open the laptop and realized that the antena cables were not plugged on the wireless card... Very strange for a new Lenovo laptop!

Now everything is working fine!

Best regards and thanks for your support!:D

---

