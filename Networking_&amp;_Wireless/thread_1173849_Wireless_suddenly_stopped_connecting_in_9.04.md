---
title: "Wireless suddenly stopped connecting in 9.04"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by Gen. Lee poor on 2009-05-30
Hi. 

I hope someone can help me with a troubling network problem I got. 
I bought this HP pavilion DV7 back in December, and have been dual booting with Vista and Ubuntu (8.10, and then recently upgraded to 9.04). 
The wireless has been working fine with my SSID (MOES-BAR in the samples below), but the last 2 days, it simply refuses to connect. The wired connection works fine (posting from now) when putting network cable into wireless router, and if I boot in Vista, all works fine too. But ubuntu looks likes it's just "stopped working". I can't see that I've changed anything on the system, and the update manager has nothing new to suggest that a recent update broke the setup. 

It basically tries for about 20 seconds to connect, and then pops up with the password prompt, which is already filled in (I've tried just clicking ok, and also retyping it), and then hangs for another 20-30 secs before either asking for the password again, or giving up.

I've seen suggestions to post a few outputs from commands in response to other questions, so here they are (these are taken while wired net is unplugged, and wireless is normally trying to connect. 

**nigel@Homer:~$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:34:53:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:ba:9d:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:ba:6e:f7:7a:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



**nigel@Homer:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MOES-BAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:EF:9D:A1   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=87/100  Signal level:-46 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**nigel@Homer:~$ sudo iwlist scanning**

[sudo] password for nigel: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:E9:B9:BD:A9
                    ESSID:"Amalienborg"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level:-80 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 000B416D616C69656E626F7267
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 07064E4F20010D0D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
                    IE: Unknown: DD07000393016A0120
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003aa409d6177
                    Extra: Last beacon: 764ms ago
          Cell 02 - Address: 00:11:24:61:BF:8D
                    ESSID:"Apple Network 61bf8d"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00144170706C65204E6574776F726B20363162663864
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0700039301660000
                    IE: Unknown: DD06001018020000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000062b1c40297
                    Extra: Last beacon: 828ms ago
          Cell 03 - Address: 00:24:8C:17:7C:6F
                    ESSID:"49RNq9TX"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=76/100  Signal level:-58 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00083439524E71395458
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000b5b04e3fc
                    Extra: Last beacon: 528ms ago
          Cell 04 - Address: 00:13:49:EF:9D:A1
                    ESSID:"MOES-BAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=84/100  Signal level:-49 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00084D4F45532D424152
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0408002800
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000007eaf41cc
                    Extra: Last beacon: 308ms ago
          Cell 05 - Address: 00:02:CF:92:2E:1E
                    ESSID:"UnniOva"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 0007556E6E694F7661
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000012aae7381cd
                    Extra: Last beacon: 516ms ago
          Cell 06 - Address: 00:1E:58:84:30:7B
                    ESSID:"Goldhinkel"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 000A476F6C6468696E6B656C
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A000110103B00010310470010A15E5CB8C0CE58D0F6E1001E5884307B104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003c6b49181
                    Extra: Last beacon: 672ms ago
          Cell 07 - Address: 00:0F:CC:DD:C3:54
                    ESSID:"Internet"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/100  Signal level:-80 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 0008496E7465726E6574
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000093666768a
                    Extra: Last beacon: 448ms ago
          Cell 08 - Address: 00:1E:52:79:E1:84
                    ESSID:"Franz Cybulskis Netværk"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=57/100  Signal level:-74 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00184672616E7A20437962756C736B6973204E657476C3A6726B
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609000800000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409000800000000000000000000000000000000000000
                    IE: Unknown: DD0700039301690020
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003a7c2483f
                    Extra: Last beacon: 460ms ago
          Cell 09 - Address: 00:50:FC:F4:25:4F
                    ESSID:"Gadsnet"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 0007476164736E6574
                    IE: Unknown: 010882848B960C18306C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 320412244860
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 54 Mb/s; 9 Mb/s; 18 Mb/s
                              36 Mb/s; 48 Mb/s
                    Extra:tsf=00000072bd9a3203
                    Extra: Last beacon: 168ms ago
          Cell 10 - Address: 00:18:F8:64:80:49
                    ESSID:"Krabbe"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=78/100  Signal level:-56 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00064B7261626265
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 1218243048606C3FCB6400218B40420F000000000080841E0000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000182c6c9f181
                    Extra: Last beacon: 212ms ago
          Cell 11 - Address: 00:1E:E5:43:BF:ED
                    ESSID:"PHNET"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 000550484E4554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000188af102309
                    Extra: Last beacon: 372ms ago
          Cell 12 - Address: 00:1A:2A:2E:23:65
                    ESSID:"is"
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-127 dBm
                    Encryption key: off
                    IE: Unknown: 00026973
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003fd08b47cd
                    Extra: Last beacon: 80ms ago
          Cell 13 - Address: 00:1E:2A:54:D0:A8
                    ESSID:"kennel"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00066B656E6E656C
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000143d9912e2
                    Extra: Last beacon: 388ms ago
          Cell 14 - Address: 00:17:F2:E4:48:EF
                    ESSID:"MacMads"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00074D61634D616473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0700039301660000
                    IE: Unknown: DD06001018020100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000db85547978
                    Extra: Last beacon: 820ms ago
          Cell 15 - Address: 00:1C:DF:97:69:94
                    ESSID:"CB"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key: on
                    IE: Unknown: 00024342
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 051300010001000000000000000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002678c654183
                    Extra: Last beacon: 816ms ago

pan0      Interface doesn't support scanning.


Many thanks in advance for any help. 
Nigel

---

### Post by lisati on 2009-05-30
Could be a conflict with a neighbouring network. I notice your one and another both use channel 6. This is usually set within the router.

---

### Post by Gen. Lee poor on 2009-05-30
I'll take a look, but there have been lots of networks around for some months now and I don't think this has changed. 
Mind you, I have just seen this big thread regarding general wireless problems in 9.04 (Sorry, I didn't spot it before posting), so I'll try installing linux-backports-modules-jaunty before checking it again

---

### Post by Gen. Lee poor on 2009-05-30
One reboot later, and it connects first time now. 
So it seems that it is related to this issue

[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Sorry for adding to the clutter of threads on this issue

---

