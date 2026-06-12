---
title: "PRO/Wireless 3945ABG not detecting a network"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by kalajalaluu on 2012-01-31
Here is the issue I hope you can help me with. My laptop will not detect one specific wireless network. It wouldn't much of an issue would not this be the wireless where I live at. Works fine with other wifis I've tried. Mac filtering is enable but mine is added to the router so this shouldn't be the problem.

There is also a second thing which could be related. Every time I close the laptop lid (or hibernate or suspend) the laptop it will not able to detect any wirleless connections once the lid is reopened.

I'm running 10.04 right now but I had the same problems with 11.10 as well.

The kernel is 2.6.32-38-generic i686


I thought it would be a good idea to perhaps replace the driver but I wasn't able to find information about that. Is there something with this kind of reasoning?

Here's some more information:

```
markku@markku-laptop:~$ lspci -nn | grep Network
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

```
markku@markku-laptop:~$ iwconfig wlan1
wlan1     IEEE 802.11abg  ESSID:"Nurk"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:C3:C5:F4   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm not sure which part of the lsmod I should be posting, so I'm "grepping" the driver name.

```
markku@markku-laptop:~$ lsmod | grep iwl
iwl3945                68727  0 
iwlcore               106149  1 iwl3945
mac80211              205434  2 iwl3945,iwlcore
led_class               2864  2 iwl3945,iwlcore
cfg80211              126528  3 iwl3945,iwlcore,mac80211
```

```
markku@markku-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1F:9F:C3:C5:F4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Nurk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ae0ac843
                    Extra: Last beacon: 71440ms ago
                    IE: Unknown: 00044E75726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

Thanks for considering,

kalajalaluu

---

### Post by kalajalaluu on 2012-02-10
The lubuntu prefix is a mistake, it's meant to be just ubuntu.

---

