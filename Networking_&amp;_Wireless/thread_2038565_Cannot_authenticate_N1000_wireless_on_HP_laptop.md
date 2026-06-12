---
title: "Cannot authenticate N1000 wireless on HP laptop"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by dbNoWindows on 2012-08-06
Hi, I have an HP DV6000 series with Intel N1000 wireless card. Dual - OS Windows7 and Ubuntu 12.04, upgraded from 11.10.
I have been successfully using all wireless functions in both Windows and 12.04 up until recently. After running some security updates for Ubuntu,  I cannot authenticate WPA2 personal. System sees all networks, can connect via ethernet. Can connect to wireless and ethernet in Windows.
I have been reading a lot of threads and followed some instructions from some. I have downgraded my driver from release 05 to 03, I have run -n command in modprobe.d. I have loaded alternate network managers, I have deleted all connections and re-installed them. I have tried to connect with a bootable Kubuntu 11.10 CD - all with no success.
I am using a Billion 7402nx modem/router.
My partner has an identical laptop running dual OS. Windows 7 and Ubuntu 11.10, and _can_ connect wireless from both OS. Her system has had no upgrades or updates.
I have tried using WEP and no security on the router, with no success.
I have a Netcom router at another location that I can no longer connect to either.
I used to connect to all my routers in 12.04 up until doing some security updates 2 weeks ago. Now it tries to connect but cannot authenticate.

Below are some outputs that may be helpful.

david@DavidsHP:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux DavidsHP 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
david@DavidsHP:~$ 

david@DavidsHP:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:aa:b1:8a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:91:bb:86
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-27-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff
david@DavidsHP:~$ 

david@DavidsHP:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        8C:A9:82:91:BB:86
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 
    Gebie:           Infra, 00:1D:AA:A5:5A:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    COC Network:     Infra, 00:23:6C:BE:CF:23, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    FF502594:        Infra, 00:60:B3:8D:F61, Freq 2462 MHz, Rate 11 Mb/s, Strength 25 WPA
    Jimojo Internet Hotspot: Infra, 00:02:6F:52:E7:9B, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    HOLMES_CNS:      Infra, 00:1F:28:C4:C:29, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    HOLMES_CNS:      Infra, 00:11:85:AD:FA:1F, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 Enterprise
    LASTRESORTCAIRNS:Infra, 1C:BD:B9:32:78:74, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Coffee Bean on Lake: Infra, AC:86:74:04:AF:2A, Freq 2432 MHz, Rate 54 Mb/s, Strength 100
    CBE Lake Private:Infra, 00:04:ED:EA:2D:9D, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        2C:27:7:AA:B1:8A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


david@DavidsHP:~$ 
david@DavidsHP:~$ iwconfig
lo        no wireless extensions. 
wlan0     IEEE 802.11bgn  ESSID ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Management ff
            
eth0      no wireless extensions.


david@DavidsHP:~$ lspci -nm | grep 0280
0d:00.0 "0280" "8086" "0084" "8086" "1315"


david@DavidsHP:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
david@DavidsHP:~$ 



david@DavidsHP:~$ sudo iwlist scan
[sudo] password for david: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:EA:2D:9D
                    Channel:3
                    Frequency:2.422 GHz (Channel 3) 
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption keyn
                    ESSID:"CBE Lake Private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001057679158
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0010434245204C616B652050726976617465
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000B127A
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:1F:28:C4:C:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:n
                    ESSID:"HOLMES_CNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000325002e9181
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 000A484F4C4D45535F434E53
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010640
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0106
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: 1C:BD:B9:32:78:74
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:n
                    ESSID:"LASTRESORTCAIRNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008e05a56c144
                    Extra: Last beacon: 8776ms ago
                    IE: Unknown: 00104C4153545245534F5254434149524E53
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 05050001001805
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020008127A
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 02:CA:FE:CA:CA:40
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key;ff
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000195d24f4
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030105
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D16050400000000FF000000000000000000000000000000
                    IE: Unknown: DD070050F202000100
          Cell 05 - Address: 00:1D:AA:A5:5A:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key;n
                    ESSID:"Gebie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000017d4fa143
                    Extra: Last beacon: 452ms ago
                    IE: Unknown: 00054765626965
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B28601001DAAA55AF8103C000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1606070600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001187A12
                    IE: Unknown: DD1E00904C336E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 06 - Address: 00:02:6F:52:E7:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:ff
                    ESSID:"Jimojo Internet Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000645046186
                    Extra: Last beacon: 9084ms ago
                    IE: Unknown: 00174A696D6F6A6F20496E7465726E657420486F7473706F74
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101david@DavidsHP:~$ sudo iwlist scan
[sudo] password for david: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:EA:2D:9D
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:n
                    ESSID:"CBE Lake Private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001057679158
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0010434245204C616B652050726976617465
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000B127A
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:1F:28:C4:C:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:n
                    ESSID:"HOLMES_CNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000325002e9181
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 000A484F4C4D45535F434E53
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010640
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0106
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: 1C:BD:B9:32:78:74
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:n
                    ESSID:"LASTRESORTCAIRNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008e05a56c144
                    Extra: Last beacon: 8776ms ago
                    IE: Unknown: 00104C4153545245534F5254434149524E53
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060david@DavidsHP:~$ sudo iwlist scan
[sudo] password for david: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:EA:2D:9D
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CBE Lake Private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001057679158
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0010434245204C616B652050726976617465
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000david@DavidsHP:~$ sudo iwlist scan
[sudo] password for david: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:EA:2D:9D
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CBE Lake Private"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001057679158
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0010434245204C616B652050726976617465
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000B127A
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:1F:28:C4:C:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOLMES_CNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000325002e9181
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 000A484F4C4D45535F434E53
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010640
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0106
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: 1C:BD:B9:32:78:74
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"LASTRESORTCAIRNS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008e05a56c144
                    Extra: Last beacon: 8776ms ago
                    IE: Unknown: 00104C4153545245534F5254434149524E53
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 05050001001805
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020008127A
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 02:CA:FE:CA:CA:40
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000195d24f4
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030105
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D16050400000000FF000000000000000000000000000000
                    IE: Unknown: DD070050F202000100
          Cell 05 - Address: 00:1D:AA:A5:5A:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Gebie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000017d4fa143
                    Extra: Last beacon: 452ms ago
                    IE: Unknown: 00054765626965
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545720010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010110470010BC329E001DD811B28601001DAAA55AF8103C000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1606070600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001187A12
                    IE: Unknown: DD1E00904C336E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406070600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 06 - Address: 00:02:6F:52:E7:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    
                    ESSID:"Coffee Bean on Lake"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000195dc180
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0013436F66666565204265616E206F6E204C616B65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

david@DavidsHP:~$ 

                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000B127A
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:1F:28:C4:C:29
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000195d24f4
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030105
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D16050400000000FF000000000000000000000000000000
                    IE: Unknown: DD070050F202000100
          Cell 05 - Address: 00:1D:AA:A5:5A:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    
                    ESSID:"Coffee Bean on Lake"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000195dc180
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0013436F66666565204265616E206F6E204C616B65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

david@DavidsHP:~$ 

                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 05050001001805
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020008127A
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 02:CA:FE:CA:CA:40
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000000195d24f4
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030105
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D16050400000000FF000000000000000000000000000000
                    IE: Unknown: DD070050F202000100
          Cell 05 - Address: 00:1D:AA:A5:5A:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    
                    ESSID:"Coffee Bean on Lake"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000195dc180
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0013436F66666565204265616E206F6E204C616B65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706415520010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

david@DavidsHP:~$ 

                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD2A000C42000000011E0000000000661C0300004D41494E524F555445520000000000000000000005026C09
          Cell 07 - Address: 00:23:6C:BE:CF:23
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    
eth0      Interface doesn't support scanning.

david@DavidsHP:~$ 



david@DavidsHP:~$ lsmod | grep -e laptop -e wmi
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 hp_wmi
david@DavidsHP:~$ 

Regards

---

### Post by dbNoWindows on 2012-08-08
I have finally resolved my issue. There are quite a few users who are having wireless networking issues with 11.10 and 12.04, and they probably will with 12.10
I have researched this issue for many many hours, read many many many forums and have found only 3 common denominators to the problem.
1. laptops
2. Kernel 3.0 and 3.2
3. Different operating systems. e.g Red Hat, Suse and Ubuntu

Here's the kicker. Some users with 12.04 may never experience the problem, while others will never be able to get wireless on kernel 3 +.

I was using 11.04, then 11.10 then I moved to 12.04. for several months I have never had a problem with wireless networking - up until the other week. Suddenly it would not connect. I could see all networks but could not authenticate.

What is the only other common denominator ???  Portability. I will bet a dollar that the people who have the wireless issue are users that move their notebooks through different routers.

In my business I shift between 3 routers, plus on occasions a pocket router and recently I have had to use my phone as a network access point.

Recently I had to wait for 14 days for Telstra to connect broadband to my line. During this time I had to print to the office network and also get to the internet. To do this I used the Billion router to print, and then to get to the internet I switched to my phone as a hot spot. I was doing this many times per day for over a week. During this time, I observed that the wireless connection was at times behaving strangely, e.g sometimes I had to re-boot to get a wireless connection again. Then recently it stopped altogether. I could not connect to wireless.

People have been blaming network manager, Intel, driver versions,  plus a variety of other things, all - to no avail. I personally believe that the issue lies within the kernel of 3+ 

Until that issue is addressed the problem will continue for many Linux users.

My resolution was to re-install 11.04. I have done this and my system is working just fine.

---

