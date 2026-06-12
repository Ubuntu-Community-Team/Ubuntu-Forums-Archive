---
title: "Intel 3956ABG wireless not working with WPA"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by spong107 on 2011-10-20
I have a Thinkpad T60 that I upgraded to Ubuntu 11.10 from 11.04. 

The wireless worked in 11.04. In 11.10, it detects the wireless networks available, and can connect to non-encrypted networks. However, when I try to connect to my network which uses WPA2-Personal, I can enter the passphrase, but then it won't connect to it.

How can this be fixed?

Thanks.

Information:

```

$ lspci -nn | grep 'Wireless'
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:13:02:ba:c4:52  
          inet6 addr: fe80::213:2ff:feba:c452/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1187653 (1.1 MB)  TX bytes:248063 (248.0 KB)


$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:aa:3f:b5
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:ba:c4:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:edf00000-edf00fff

$ lsb_release -d
Description:	Ubuntu 11.10

$ uname -mr
3.0.0-12-generic i686

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                            [ OK ]


```

---

### Post by wildmanne39 on 2011-10-20
Hi, please post the results of these commands here:
```
nm-tool
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwconfig
```
```
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n35
```
Thank you

---

### Post by spong107 on 2011-10-20
Here is the info:

```

$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:16:41:AA:3F:B5

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:13:02:BA:C4:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE843:        Infra, B0:E7:54:70:5D:59, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WEP
    linksys:         Infra, 00:1A:70:E7:74:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    wireless:        Infra, A0:21:B7:6B:B7:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    2WIRE654:        Infra, 34:EF:44:96:07:19, Freq 2417 MHz, Rate 54 Mb/s, Strength 25 WEP
    2WIRE663:        Infra, 00:14:95:7D:9C:79, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    Aaron's Network: Infra, 10:9A:DD:82:8E:D3, Freq 2442 MHz, Rate 54 Mb/s, Strength 17 WPA2
    NETGEAR:         Infra, 00:1E:2A:50:97:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    CHARLIE:         Infra, C0:3F:0E:55:C0:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Craig&Cali:      Infra, 00:1F:F3:C1:D3:CE, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    T.W.C7:          Infra, 00:26:F2:23:55:FD, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Mother of Steve: Infra, 00:21:29:D3:19:0C, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    9Amanda9:        Infra, 90:84:0D:DB:7F:A5, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Joker:           Infra, 00:1B:2F:0D:C9:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    eden123:         Infra, 98:FC:11:B8:06:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    9Amanda9:        Infra, 90:84:0D:DB:7F:A6, Freq 5745 MHz, Rate 54 Mb/s, Strength 37 WPA2
    cooljazz:        Infra, 00:24:01:3F:7B:4C, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA
    CGD24GE9:        Infra, E0:91:F5:85:39:6C, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    525:             Infra, 00:18:39:D9:E9:33, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2


$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:3F:7B:4C
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"cooljazz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005bacb18c180
                    Extra: Last beacon: 2196ms ago
                    IE: Unknown: 0008636F6F6C6A617A7A
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340300030000000F000000000000000000000000000000
          Cell 02 - Address: 00:18:39:D9:E9:33
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"525"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d4541f582
                    Extra: Last beacon: 1904ms ago
                    IE: Unknown: 0003353235
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 03 - Address: 98:FC:11:B8:06:1A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"eden123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007f0fc91e
                    Extra: Last beacon: 1944ms ago
                    IE: Unknown: 00076564656E313233
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100098FC11B8061A102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B4334393831381054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: C0:C1:C0:7B:A0:D5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000807386d186
                    Extra: Last beacon: 1892ms ago
                    IE: Unknown: 000D00000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0504FEFF0000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 05 - Address: 00:14:95:7D:9C:79
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"2WIRE663"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c376d181
                    Extra: Last beacon: 1904ms ago
                    IE: Unknown: 00083257495245363633
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 06 - Address: 00:1A:70:E7:74:F9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000064b6c34e7ef
                    Extra: Last beacon: 2004ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 07 - Address: E0:91:F5:85:39:6C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CGD24GE9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024c29357c8
                    Extra: Last beacon: 1728ms ago
                    IE: Unknown: 00084347443234474539
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010D3A25A469459E76E2F7C1A2499C2AC4D102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 90:84:0D:DB:7F:A5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"9Amanda9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005bc031bc1d0
                    Extra: Last beacon: 1732ms ago
                    IE: Unknown: 000839416D616E646139
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
                    IE: Unknown: DD1700039301720120000E90840DDB7FA50B90840DDB7FA695
                    IE: Unknown: DD070017F203020180
          Cell 09 - Address: 00:1E:2A:50:97:86
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000031c2480181
                    Extra: Last beacon: 5888ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: C0:3F:0E:51:86:8A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"SR Netgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e0521f219d
                    Extra: Last beacon: 2272ms ago
                    IE: Unknown: 000A5352204E657467656172
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700108B7B3FF3F66C9CEE882BF8731DC009F01021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 00:26:F2:23:55:FD
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"T.W.C7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003048ece18f
                    Extra: Last beacon: 1712ms ago
                    IE: Unknown: 0006542E572E4337
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: 90:84:0D:DB:7F:A6
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"9Amanda9"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005bc03e55032
                    Extra: Last beacon: 4760ms ago
                    IE: Unknown: 000839416D616E646139
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 050400030000
                    IE: Unknown: 070A55532024041E95051E00
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEE0117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1695050000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE0117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3495050000000000000000000000000000000000000000
                    IE: Unknown: DD1700039301720120000E90840DDB7FA50B90840DDB7FA695
                    IE: Unknown: DD070017F203020180
          Cell 13 - Address: 00:1B:2F:0D:C9:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Joker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003270b2097b
                    Extra: Last beacon: 1996ms ago
                    IE: Unknown: 00054A6F6B6572
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101000002A44000
                    IE: Unknown: DD1A00037F0301000000001B2F0DC9F8021B2F0DC9F864002C011D08
          Cell 14 - Address: 34:EF:44:96:07:19
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"2WIRE654"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000835004181
                    Extra: Last beacon: 7020ms ago
                    IE: Unknown: 00083257495245363534
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 15 - Address: 00:1E:E5:FA:CA:55
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"grnrcr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004c220d1e97d
                    Extra: Last beacon: 2320ms ago
                    IE: Unknown: 000667726E726372
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000100000000000000000000000000000000000000
          Cell 16 - Address: 00:26:50:4E:6D:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"2WIRE738"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000106f48f1181
                    Extra: Last beacon: 6480ms ago
                    IE: Unknown: 00083257495245373338
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 17 - Address: B0:E7:54:70:5D:59
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"2WIRE843"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004d8a02a2
                    Extra: Last beacon: 2164ms ago
                    IE: Unknown: 00083257495245383433
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 18 - Address: 00:21:29:D3:19:0C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Mother of Steve"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000334ac66b183
                    Extra: Last beacon: 6580ms ago
                    IE: Unknown: 000F4D6F74686572206F66205374657665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: 58:6D:8F:2B:57:2A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Action Jackson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000103fc1eba84
                    Extra: Last beacon: 2392ms ago
                    IE: Unknown: 000E416374696F6E204A61636B736F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD860050F204104A0001101044000102103B00010310470010EC53B0E308858BE55944CC185D19DDF6102100074C696E6B7379731023000D4C696E6B7379732045333230301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204533323030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ lsmod | grep iwl
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211


$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n35
Oct 20 11:28:31 Foo kernel: [  114.927392] wlan0: direct probe responded
Oct 20 11:28:31 Foo kernel: [  114.932150] wlan0: authenticate with c0:3f:0e:51:86:8a (try 1)
Oct 20 11:28:31 Foo kernel: [  114.941511] wlan0: authenticated
Oct 20 11:28:31 Foo kernel: [  114.942260] wlan0: associate with c0:3f:0e:51:86:8a (try 1)
Oct 20 11:28:31 Foo kernel: [  114.944726] wlan0: RX AssocResp from c0:3f:0e:51:86:8a (capab=0x401 status=0 aid=3)
Oct 20 11:28:31 Foo kernel: [  114.944733] wlan0: associated
Oct 20 11:28:31 Foo kernel: [  114.947820] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 11:28:31 Foo NetworkManager[787]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 20 11:28:31 Foo NetworkManager[787]: <info> (wlan0): supplicant interface state: associating -> completed
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SR Netgear'.
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 20 11:28:31 Foo NetworkManager[787]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 20 11:28:31 Foo NetworkManager[787]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 20 11:28:31 Foo dhclient: Listening on LPF/wlan0/00:13:02:ba:c4:52
Oct 20 11:28:31 Foo dhclient: Sending on   LPF/wlan0/00:13:02:ba:c4:52
Oct 20 11:28:31 Foo dhclient: DHCPREQUEST of 10.0.0.20 on wlan0 to 255.255.255.255 port 67
Oct 20 11:28:31 Foo NetworkManager[787]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 20 11:28:31 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 20 11:28:32 Foo NetworkManager[787]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 20 11:28:32 Foo NetworkManager[787]: <info> Policy set 'SR Netgear' (wlan0) as default for IPv4 routing and DNS.
Oct 20 11:28:32 Foo NetworkManager[787]: <info> Activation (wlan0) successful, device activated.
Oct 20 11:28:32 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 20 11:28:32 Foo NetworkManager[787]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 20 11:28:42 Foo kernel: [  125.672067] wlan0: no IPv6 routers present
Oct 20 11:28:44 Foo NetworkManager[787]: <info> (wlan0): device state change: activated -> disconnected (reason 'connection-removed') [100 30 38]
Oct 20 11:28:44 Foo NetworkManager[787]: <info> (wlan0): deactivating device (reason 'connection-removed') [38]
Oct 20 11:28:44 Foo NetworkManager[787]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1940
Oct 20 11:28:44 Foo kernel: [  127.756425] wlan0: deauthenticating from c0:3f:0e:51:86:8a by local choice (reason=3)
Oct 20 11:28:44 Foo NetworkManager[787]: <info> (wlan0): supplicant interface state: completed -> disconnected



```

---

### Post by wildmanne39 on 2011-10-20
Hi, what is the name of the network you are trying to connect too? so I can have a better understanding of the settings.
Thank you

---

### Post by spong107 on 2011-10-20
The network I'm trying to connect to is '525'.

Thanks.

---

### Post by wildmanne39 on 2011-10-20
Hi, try this please: Disconnect your wired connection then run these commands one line at a time and if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=1
sudo ifconfig wlan0 up
```
Thank you

---

### Post by spong107 on 2011-10-20
I ran the commands, and then tried to connect to the wireless access point, and the behavior is the same. It sees the network, I can click on it, enter the password, and then nothing happens.

---

### Post by wildmanne39 on 2011-10-20
Hi, let&#347; try this parameter then please.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo ifconfig wlan0 up
```
Thank you

---

### Post by spong107 on 2011-10-20
That didn't work either. :(

---

### Post by wildmanne39 on 2011-10-20
Hi, I have been doing research and I found some people had to change wpa2 to wep to connect, I recommend trying that and seeing if you can connect then.

You might want to reset your router.
Thank you

---

### Post by spong107 on 2011-10-20
I changed to use WEP instead of WPA2, and reset the router. Still cannot connect.

Also, even before this, I upgraded the router firmware (WRT54G v6) to the latest (1.02.8).

Even if WEP worked, I would like to have a solution that works with WPA2, as this isn't the only computer on the wireless network, nor is the laptop my main computer.

Worse case, I'll just reinstall Ubuntu 11.04.

Thanks. I appreciate all the help.

---

### Post by wildmanne39 on 2011-10-20
Hi, the point was not to leave it on wep or unsecured it was so I could narrow down the issue.

I believe it is an issue with network manager.

Please restart your computer that will make all the changes we have made go away, then install wicd using synaptic or software center then completely remove network manager but install wicd first.
```
sudo apt-get purge network-manager network-manager-gnome
```
Then see if it connects.
Thank you

---

### Post by spong107 on 2011-10-20
It worked. Thanks!

Using Wicd Network Manager is working. Now is there any Wicd taskbar icon that can be displayed to show that the wireless is connected and working?

---

### Post by wildmanne39 on 2011-10-20
Hi, I thought it would but I was being cautious.

Your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
Enjoy

---

### Post by hero1900 on 2011-11-01
here is it from 11.04 maybe it will help someone to solve this i already downgrade since nothing working for me and yet [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") i tried to use wicd and other solutions with nothing. its just bad and also had usb wireless and i used it but the net is so slow on it and less reliable keep disconnecting. so i had to go to 11.04. also need to mention that downgrading kernel will not solve any thing and it seems no one knows where is the issue. i guess i will try to boot the same kernel on 11.10 in different distribution and see if it has same issue if not then its ubuntu integration problem 

```
cat dmesg.0 | grep iw
[    7.257207] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    7.257210] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    7.257269] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.257283] iwl3945 0000:02:00.0: setting latency timer to 64
[    7.313809] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    7.313811] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.313956] iwl3945 0000:02:00.0: irq 46 for MSI/MSI-X
[    7.692073] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.233824] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9

```

---

### Post by wildmanne39 on 2011-11-01
Hi hero1900 did you also try this link?
[http://ubuntuforums.org/showthread.php?t=1859558&page=3](http://ubuntuforums.org/showthread.php?t=1859558&page=3)
Post 21.
Thank you

---

### Post by chfast on 2011-11-02
Because your network name is "525", what is a pure numeric, I think it might be this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/874328](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/874328)

The fix was released in network-manager 0.9.1.90-0ubuntu5.
I checked the fix and it solves my similar problem.

---

### Post by msumurph on 2012-01-31
> **wildmanne39 said:**
> 
Please restart your computer that will make all the changes we have made go away, then install wicd using synaptic or software center then completely remove network manager but install wicd first.
```
sudo apt-get purge network-manager network-manager-gnome
```
Then see if it connects.
Thank you

Thank you!  This fixed my issue with my Linksys WRT54G.  The computer showed that my network was available but would not connect.  After installing wicd and removing Network Manager, I'm all set. :p

---

### Post by wildmanne39 on 2012-02-01
Hi, your welcome!

---

