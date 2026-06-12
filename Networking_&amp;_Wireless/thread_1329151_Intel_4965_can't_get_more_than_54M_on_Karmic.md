---
title: "Intel 4965 can't get more than 54M on Karmic"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by zaphod777 on 2009-11-17
So I had a problem with wireless not connecting so I installed the Linux backports and it started working but not going the full 130M my router can do.

I then found that there seams to be a problem with aht5k driver being blacklisted
so I removed the backport driver and tried this

1. open /etc/modprobe.d & look for "blacklist-ath_pci.conf"
2. if it is there--open the file as root & put a # in front of "blacklist ath_pci"
3. reboot 

Wireless still connects but it seams the system thinks my router is only capable of transmitting up to 54M not the 130M I could get when running Windows on the same system. 

This is the one thing that is hanging me up and its more of an anoyance than anything but I would still like to fix it. I like to send lots of video files over the WLAN to my NAS. 

```
          Cell 06 - Address: 00:1D:73:8E:DE:98
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002adf5dc
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00023432
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A0F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD09000740010109000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD600050F204104A0001101044000102103B000103104700106CBFAD14D7C911DDBDF5435E7C97A827102100012D1023000D575A522D48502D473330304E48102400012D104200012D1054000800060050F204000110110003575053100800020086
```

```
user@computer:~$:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"42"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1D:73:8E:DE:98   
          Bit Rate=0 kb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


user@computer:~$ 

```

---

