---
title: "Wi-Fi dropping like crazy"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by TechSupportx86 on 2011-08-10
Ubuntu Server 10.10
Linksys WMP54G v4.1

I am trying to get my card to connect to my network so i can move it to the basement. I got it to where it will connect to the AP on start-up, and then i can use it for about 3 minutes then it just drops connection. I get a good signal from the AP since it is about 10 feet away, but it still refuses to stay connected.

I have been reading alot of forums and alot of people seem to be having this problem with 10.10. I would just install 11.04, but i already got it configured the way i need it via SSH through eth0.

Any ideas?

---

### Post by lkjoel on 2011-08-10
Could you give me the output of these Terminal commands?
```
sudo ifconfig
sudo iwconfig
sudo rfkill list all
sudo nm-tool
sudo iwlist scan

```

---

### Post by TechSupportx86 on 2011-08-10
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:0b:d4:b0
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe0b:d4b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:449269 (449.2 KB)  TX bytes:364649 (364.6 KB)
          Interrupt:23 Base address:0xdf00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1316 (1.3 KB)  TX bytes:1316 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:f8:2e:0a:7a
          inet addr:192.168.2.120  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fe2e:a7a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1260 (1.2 KB)  TX bytes:576 (576.0 B)

``````
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

``````
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm
                    Encryption key:on
                    ESSID:"Calvin's-Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a52ffcbab
                    Extra: Last beacon: 792ms ago
                    IE: Unknown: 001043616C76696E27732D4E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F0010000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 02 - Address: 00:0F:66:8B:99:6F
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=50/70  Signal level=-60 dBm
                    Encryption key:on
                    ESSID:"Delarosa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000002cf02bc5f8
                    Extra: Last beacon: 704ms ago
                    IE: Unknown: 000844656C61726F7361
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030107
                    IE: Unknown: 0406000200000000
          Cell 03 - Address: 00:22:3F:22:C7:A0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c9b035181
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 000A00000000000000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 0C:D5:02:12:69:55
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm
                    Encryption key:on
                    ESSID:"10FX08137903"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000792f961b08
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 000C313046583038313337393033
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
          Cell 05 - Address: 00:23:97:8B:25:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm
                    Encryption key:on
                    ESSID:"DominicanNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ae70ab397
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 0010446F6D696E6963616E4E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
          Cell 06 - Address: 00:23:97:60:5F:7A
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=52/70  Signal level=-58 dBm
                    Encryption key:on
                    ESSID:"simba"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019a7477183
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 000573696D6261
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 98:FC:11:B9:56:1E
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm
                    Encryption key:on
                    ESSID:"squeaky"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000053de4306f
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000773717565616B79
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
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
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100098FC11B9561E102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B4336373334341054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 00:23:97:90:32:3E
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm
                    Encryption key:on
                    ESSID:"verizon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009eff21bd13
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 0007766572697A6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
          Cell 09 - Address: E0:91:F5:AF:ED:08
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-40 dBm
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000493a31d80
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400020100
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A0F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD2C0050F204104A000110104400010210570001011047001000000000000010000000E091F5AFED08103C000103
          Cell 10 - Address: 00:21:29:A0:B0:7B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm
                    Encryption key:on
                    ESSID:"ryu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017eff03f183
                    Extra: Last beacon: 452ms ago
                    IE: Unknown: 0003727975
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 11 - Address: 00:18:3A:B0:D0:23
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm
                    Encryption key:on
                    ESSID:"jasan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000920774f0ec1
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 00056A6173616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000

```

Can't install nm-tool because i only have network access ATM.

---

### Post by lkjoel on 2011-08-10
Download the attachment into your home directory.
When Wifi drops, type this into a Terminal window:
```
cd ~
chmod +x wireless.sh
./wireless.sh wlan0 *NETWORKNAME*

```

---

### Post by TechSupportx86 on 2011-08-10
Well that does re-establish connection, but it loses it again shortly after :/

Got anything else? If not i think i'll just try 11.04

---

### Post by lkjoel on 2011-08-10
Not really, except make a bash script like this:
```
#!/bin/bash
cd ~
while true
do
./wireless.sh wlan0 *NETWORKNAME*
sleep 60
done &

```It will automatically run the wireless script every 60 seconds.

---

### Post by nm_geo on 2011-08-10
Could we see

```
lspci -nn | grep 0280
``````
lsmod
``````
sudo lshw -C network
```Just curious here....

---

