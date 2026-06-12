---
title: "iwlwifi drops network connections."
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by ulugeyik on 2013-05-16
Hello,

I have tried the ASUS support section with no luck. I am using a ASUS Zenbook UX31A  with Ubuntu 12.10 installed. I have no wireless problems at work or at home but I have been at a hospital with a wireless connection (WPA & WPA2 Personal) for the last week and I lose connection every few minutes and I have to disconnect/reconnect multiple times. First, I was blaming the hospital itself but then I tried my other Asus netbook (12.04 installed) which does not have this problem. Neither do any of the android tablets I use.

The only  thing I see in the logs is this transition:
[ 1800.409328] iwlwifi 0000:02:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1800.409387] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

Issuing  'sudo iwconfig wlan0 power off' seemed to have helped once but it is not persistent. It lasted a bit longer may be accidentally.

A lot of discussions on internet has suggested that I do this:
sudo rmmod iwldvm
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1 swcrypto=1

But that is also not useful. "11n_disable=1" allowed me to have significantly higher upload/download rates at home.


I do not know how to diagnose this problem and it is bugging me a lot since I am trying to work during a lenghy hospital stay. Any advice, pointers is greatly appreciated.

thanks,

---

### Post by praseodym on 2013-05-16
Please show these outputs:
```

ifconfig -a
iwconfig
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
route -n
```

---

### Post by ulugeyik on 2013-05-16
Hi,

Thanks. Here they are:

[I TRIMMED THE ESSID]

```


> ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1894008 (1.8 MB)  TX bytes:1894008 (1.8 MB)

wlan0     Link encap:Ethernet  HWaddr c4:85:08:10:d0:8d  
          inet addr:192.168.1.154  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::c685:8ff:fe10:d08d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144278035 (144.2 MB)  TX bytes:17314894 (17.3 MB)

>  iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"TP"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 1A:24:01:10:D0:8D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0

> sudo iwlist scan  
wlan0     Scan completed :
          Cell 01 - Address: 1A:24:01:10:D0:8D
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TP"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fade8542
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D54656B6E6F6E50617469656E74
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 070A455320240814640B1B00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004070000000106000CE607A6490404020000000504006C000009083D3EDDFAC22300000A04010000000B04060000000C03002800
          Cell 02 - Address: 1A:24:01:10:D0:8D
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2f98d3304
                    Extra: Last beacon: 26104ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 070A455320240814640B1B00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404020000000504008C0000090897048CF9C22300000A04010000000B04060000000C03002800
          Cell 03 - Address: 16:01:01:10:D0:8D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TP2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb296e647
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000A54656B6E6F6E50726F66
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600040B0000000106000CE607A64F0404010000000504007C00000908D99995B2BE0100000A04010000000B04050000000C03002800
          Cell 04 - Address: 1A:01:01:10:D0:8D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb296eb8c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D54656B6E6F6E50617469656E74
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600040B0000000106000CE607A64F0404010000000504007C00000908679A95B2BE0100000A04010000000B04060000000C03002800
          Cell 05 - Address: 1A:01:01:4E:AD:AA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb297048b
                    Extra: Last beacon: 4948ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010300036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040B0000000106000CE607A64F0404010000000504002C00000908737495B2BE0100000A04010000000B04060000000C03002800
          Cell 06 - Address: 1A:01:01:3C:0E:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb297060b
                    Extra: Last beacon: 4948ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010C00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040B0000000106000CE607A64F0404010000000504002C000009089F7495B2BE0100000A04010000000B04060000000C03002800
          Cell 07 - Address: 16:06:01:10:D0:8D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"TP2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fb5cf99f
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000A54656B6E6F6E50726F66
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404010000000504008C00000908D8B75BFBC22300000A04010000000B04050000000C03002800
          Cell 08 - Address: 1A:06:01:10:D0:8D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"TP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fb5cfe6d
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000D54656B6E6F6E50617469656E74
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404010000000504008C0000090859B85BFBC22300000A04010000000B04060000000C03002800
          Cell 09 - Address: 1A:06:01:B5:8A:6E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fb5d4180
                    Extra: Last beacon: 4708ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010900036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404010000000504003C0000090871C45BFBC22300000A04010000000B04060000000C03002800
          Cell 10 - Address: 1A:06:01:08:3E:E1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fb5d42fe
                    Extra: Last beacon: 4708ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010900036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404010000000504003C00000908A0C45BFBC22300000A04010000000B04060000000C03002800
          Cell 11 - Address: 1A:24:01:88:6F:2E
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2f9568035
                    Extra: Last beacon: 29692ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 070A455320240814640B1B00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010E00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040F0000000106000CE607A6280404020000000504008C000009086E5455F9C22300000A04010000000B04060000000C03002800
          Cell 12 - Address: 16:24:01:10:D0:8D
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TP2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fade875f
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000A54656B6E6F6E50726F66
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 070A455320240814640B1B00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD38000CE60004130000000106000CE607A5D10404020000000504009C000009080B3EDDFAC22300000A04010000000B04050000000C03002800
          Cell 13 - Address: 1A:06:01:10:D0:8D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fba20180
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004130000000106000CE607A5D10404010000000504009C0000090878E4A0FBC22300000A04010000000B04060000000C03002800
          Cell 14 - Address: 1A:01:01:FC:49:6F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb2970304
                    Extra: Last beacon: 4936ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004050000000106000CE607A5B3040401000000050400640000090878AC95B2BE0100000A04010000000B04060000000C03002800
          Cell 15 - Address: 1A:01:01:62:A5:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb2970482
                    Extra: Last beacon: 4936ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F00036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004050000000106000CE607A5B30404010000000504006400000908A2AC95B2BE0100000A04010000000B04060000000C03002800
          Cell 16 - Address: 1A:01:01:C8:AF:CE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb2970bd1
                    Extra: Last beacon: 4932ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004070000000106000CE607A6490404010000000504006C000009088AB495B2BE0100000A04010000000B04060000000C03002800
          Cell 17 - Address: 1A:01:01:70:4F:AB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001beb297030e
                    Extra: Last beacon: 4928ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010700036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE600040B0000000106000CE607A64F0404010000000504007C0000090882C495B2BE0100000A04010000000B04060000000C03002800
          Cell 18 - Address: 1A:06:01:47:35:96
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fb5d4180
                    Extra: Last beacon: 4704ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010802040B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010880
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010100036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004110000000106000CE607A601040401000000050400440000090872CC5BFBC22300000A04010000000B04060000000C03002800
          Cell 19 - Address: 1A:24:01:04:81:A5
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000023c2fadeb036
                    Extra: Last beacon: 4016ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400010000
                    IE: Unknown: 070A455320240814640B1B00
                    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624050800000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010800036400002586000044425E0062422F00
                    IE: Unknown: DD38000CE60004070000000106000CE607A6490404020000000504001C000009088914DDFAC22300000A04010000000B04060000000C03002800

> cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.254.0   U     9      0        0 wlan0


```

---

### Post by praseodym on 2013-05-16
There are some other networks on channel 36. Try another channel with 40 MHz distance. Check "iwlist chan" for this

---

### Post by ulugeyik on 2013-05-16
Hi, 

Sorry, I do not understand what you mean or what I can do. Thanks.

---

### Post by praseodym on 2013-05-16
Enter the IP address of your router 192.168.1.1 into the browser and enter the router interface. There you should be able to change the bandwidth and the channel, see manual.

---

### Post by ulugeyik on 2013-05-16
Hello,

Sorry, as I mentioned above, this is not my home network. This is the network of a hospital, i.e. a public wifi. Due to a hospitalization, we are stuck here for weeks. As I mentioned above, none of the other computers, laptops I am using has this problem.

---

### Post by steeldriver on 2013-05-16
How exactly is 11n_disable=1 "not useful"? does it not work? do you get errors when you reload the module?

---

### Post by ulugeyik on 2013-05-16
Hi,

It does not prevent the dropped connections. It helped to increase the upload/download speed drastically at home but at hospital, I notice no changes.

---

### Post by steeldriver on 2013-05-16
Sometimes the problem in 'campus' type networks is that (in order to get wide coverage) they have multiple access points sharing the same ESSID - that can make the wireless device go crazy trying to roam to the nearest / strongest AP - sorry I don't know if there's a reliable fix but there's some more info here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1005832)

---

### Post by praseodym on 2013-05-16
For different APs with the same ESSID scan aound:
```

sudo iwlist scan
```
and add the MAC-address of the nearest AP into the field "BSSID" in the network-manager applet.

---

### Post by ulugeyik on 2013-05-16
Hmm. It sounds similar but I can't find a solution :<

---

### Post by ulugeyik on 2013-05-16
> **praseodym said:**
> For different APs with the same ESSID scan aound:
```

sudo iwlist scan
```
and add the MAC-address of the nearest AP into the field "BSSID" in the network-manager applet.

Thanks. I am trying this now.

---

### Post by ulugeyik on 2013-05-22
The solution mentioned has worked. By choosing which device to connect to explicitly, there are no more drops.

---

