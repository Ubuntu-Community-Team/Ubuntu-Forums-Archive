---
title: "Dell 1390 will not connect to WPA/WPA2 (DD-WRT)"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by lex3001 on 2011-05-06
Hi,

I just installed Ubuntu 11.04 on a Dell D630 which has the Dell 1390 wireless adapter (which I understand is really some sort of Broadcom).

I can see all the wireless networks in the neighborhood but I cannot connect to mine. My network is running DD-WRT and uses Personal WPA/WPA2.

I was wondering if anyone has any ideas? This may be a compatibility problem between the 1390 and the router as my neighbor who has a simialr Dell D620 with a 1300 series wireless adapter has the same problem under Windows. However our E6400, other laptops, Wii, and phones do not have any trouble.

Thanks in advance...

---

### Post by josephmills on 2011-05-06
> **lex3001 said:**
> Hi,

I just installed Ubuntu 11.04 on a Dell D630 which has the Dell 1390 wireless adapter (which I understand is really some sort of Broadcom).

I can see all the wireless networks in the neighborhood but I cannot connect to mine. My network is running DD-WRT and uses Personal WPA/WPA2.

I was wondering if anyone has any ideas? This may be a compatibility problem between the 1390 and the router as my neighbor who has a simialr Dell D620 with a 1300 series wireless adapter has the same problem under Windows. However our E6400, other laptops, Wii, and phones do not have any trouble.

Thanks in advance...

hi there could we see a ```
rfkill list all 
```
and a ```
lspci -nn 
```
and a 
```
iwlist auth 
``` thanks

---

### Post by birdr on 2011-10-27
Hi, I have the same problem on a Dell Studio on Ubuntu 11.10. I can see lots of other networks in the area, but not my own.
- I cannot see the SSID in the 2.4ghz band, and cannot manually connect via selecting hidden network
- I can see the SSID for 5ghz band but cannot get a connection (I enter the password, but connection fails).
Neither work if security is disabled either.
The router is a linksys e3000 running dd-wrt, and works with all other devices, including the same machine on windows 7, phones, and other laptops. The machine is a brand new 11.10 install, and I have tried installing / reinstalling the proprietary broadcom STA drivers, and following the manual install process described on the broadcom site.
Interestingly I can connect to a tethering network created by my android phone.

```
$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
``````
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0]
02:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
04:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
07:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
07:00.1 System peripheral [0880]: Ricoh Co Ltd Memory Stick Host Controller [1180:e230] (rev 01)
07:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
07:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd FireWire Host Controller [1180:e832] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)

``````
$ iwlist auth
lo        no authentication information.

eth0      no authentication information.

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP

```I hope someone can help - I'm at a total loss! Thx.

---

### Post by birdr on 2011-10-27
After more browsing I discovered that there is a bug in 11.10 with 102.11 mode N setting in the 2.4ghz band (set to G only works), and similarly setting the 5ghz band to N (not mixed with A) solves the issue.

Not a perfect solution, but means that  I'm now working again...

---

### Post by praseodym on 2011-10-27
Please show the outputs of

```
iwconfig
sudo iwlist scan
lsmod
```
You may (only) need to blacklist the modules bcma, brcm80211, and brcmsmac with the STA driver used.

---

### Post by birdr on 2011-10-27
Hi, as requested - this is after changing the router settings as I described.
Thx for help!

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Towersnet5k"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:4C:C1:C6   
          Bit Rate=144.4 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

``````
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:D8:70:BC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001148e57b5e
                    Extra: Last beacon: 3236ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706484B20010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1609000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050300A2127A
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:01:38:D8:70:BD
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"pccwqnrej"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001148ea2a37
                    Extra: Last beacon: 2928ms ago
                    IE: Unknown: 000970636377716E72656A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1609000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050300A2127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706484B20010D10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409000700000000000000000000000000000000000000
          Cell 03 - Address: C0:C1:C0:4C:C1:C6
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Towersnet5k"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003bf0211c
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000B546F776572736E6574356B
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6C081BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:25:9C:14:AA:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"HowardHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000873fba5146a
                    Extra: Last beacon: 2904ms ago
                    IE: Unknown: 000A486F77617264486F6D65
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700104B65E0040D74B6A534222384881220291021000C4C696E6B73797320496E632E102300075752543332304E1024000776312E302E30321042000234321054000800060050F2040001101100075752543332304E100800020084
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:25:9C:0A:15:B2
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"wshome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000170de3696a
                    Extra: Last beacon: 3220ms ago
                    IE: Unknown: 00067773686F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 070C55532001021B0307140A021B
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B000103104700100000000000000001100000259C0A15B2102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30311042000A4A3932383036343030361054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
          Cell 06 - Address: B0:48:7A:E6:77:C8
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_E677C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001bc4eb76
                    Extra: Last beacon: 3516ms ago
                    IE: Unknown: 000E54502D4C494E4B5F453637374338
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD810050F204104A0001101044000101103B0001031047001000000000000010000000B0487AE677C81021000754502D4C494E4B10230009544C2D57523934304E10240003312E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523934304E100800020086103C000101
                    IE: Unknown: DD050050F20500
          Cell 07 - Address: 00:17:3F:BE:47:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"tingloveskuen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000018d3aa646
                    Extra: Last beacon: 3696ms ago
                    IE: Unknown: 000D74696E676C6F7665736B75656E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: 00:13:F7:97:B2:20
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aaac30167
                    Extra: Last beacon: 3524ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 09 - Address: 00:22:75:26:20:39
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Fools!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004515480813e
                    Extra: Last beacon: 3452ms ago
                    IE: Unknown: 0006466F6F6C7321
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AFE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: B6:74:9F:88:AF:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"rnelson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003005636b49
                    Extra: Last beacon: 3408ms ago
                    IE: Unknown: 0007726E656C736F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD960050F204104A0001101044000102103B00010310470010AEA1D3F4AAF25AFDBCDB32363B35008D1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000637383950766E104200093131313051543335331054000800060050F20400011011001F4E455456494741544F5220576972656C65737320486F6D652047617465776110080002008410570001001041000100
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 11 - Address: 00:1C:DF:03:55:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"TREE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a27793c180
                    Extra: Last beacon: 3384ms ago
                    IE: Unknown: 000454524545
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071900000000000000000000000000000000000000
                    IE: Unknown: 3D1606071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 12 - Address: 00:11:50:D1:95:DB
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Belkin_Pre-N_ED28BC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000290ab1a64
                    Extra: Last beacon: 3348ms ago
                    IE: Unknown: 001342656C6B696E5F5072652D4E5F454432384243
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD0C000AF50A0202C00003010305
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: 4C:54:99:58:8F:B6
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"gbcbf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006dba7472183
                    Extra: Last beacon: 3296ms ago
                    IE: Unknown: 00056762636266
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: 00:0D:0B:5E:1E:1E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Chang"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000bb9ae1b7
                    Extra: Last beacon: 2904ms ago
                    IE: Unknown: 00054368616E67
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

``````
lsmod
Module                  Size  Used by
rfcomm                 47946  8 
bnep                   18436  2 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
wl                   2568210  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
lib80211               14991  1 wl
bcma                   20219  0 
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
btusb                  18600  2 
bluetooth             166112  23 rfcomm,bnep,btusb
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72711  0 
fglrx                2929009  112 
mac80211              310872  1 brcmsmac
cfg80211              199587  2 brcmsmac,mac80211
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
video                  19412  0 
crc_ccitt              12667  1 brcmsmac
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi               12681  0 
dell_laptop            13831  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
psmouse                73882  0 
sparse_keymap          13890  1 dell_wmi
serio_raw              13166  0 
mei                    41480  0 
soundcore              12680  1 snd
dcdbas                 14490  1 dell_laptop
intel_ips              18089  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 dell_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
ahci                   26002  2 
firewire_core          63626  1 firewire_ohci
libahci                26861  1 ahci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci

```

---

### Post by praseodym on 2011-10-27
Blacklist these drivers:

```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot. Check afterwards additionally
```
rfkill list
```

---

### Post by birdr on 2011-10-27
I've done as described. Interestingly my 2.4ghz network stopped showing before I did this. After the change and reboot there is a much reduced list of wireless networks I can see from my neighbours. I can still connect to the 5ghz network, but cannot see my 2.4ghz network (transmitting now only on G).

```
rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Any thoughts?

---

### Post by praseodym on 2011-10-28
Blacklist the module **brcm80211**, too. Reboot after that

---

### Post by birdr on 2011-10-28
Done. Now blacklisting:
blacklist bcma
blacklist brcmsmac
blacklist brcm80211

Same issue. 
```
rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Any other suggestions - appreciate help so far!

---

### Post by pastalavista on 2011-10-28
Have you tried the solution on [this forum post]("http://ubuntuforums.org/showpost.php?p=11372158&postcount=4")?

---

### Post by birdr on 2011-10-28
Just tried. Basically stopped my wireless working. The purge command worked, but the install responded by saying I already had the latest version. A quick re-install from the additional drivers app brought my network back, but same issue as before...

---

