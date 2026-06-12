---
title: "How to connect to a wireless network and access the files in its shared folder!!"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by parvathy on 2009-04-22
hi,
Thank you for visiting this thread. I am working on ubuntu Hady Heron . I want to connect to a wireless network and access the files in the public folders of the remote system through wireless.I enabled the roaming mode of networking . i am able to see all the available wireless networks. Then i run the following commands

[B][I]# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:6B:85:C4:12
                    ESSID:"ssid_win3"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=-80 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001824daa5f76
          Cell 02 - Address: 02:1F:3B:00:16:DF
                    ESSID:"middown2-116"
                    Mode:Ad-Hoc
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=80/100  Signal level=-54 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000280a52a0a[/I][/B]

and then i tried iwconfig. i got it as

[B][I]# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"middown2-116"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:6D64-3131-36
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I][/B]

and then i don't know what to do? can anybody help me to connect to the network...Waiting for your help:(

---

