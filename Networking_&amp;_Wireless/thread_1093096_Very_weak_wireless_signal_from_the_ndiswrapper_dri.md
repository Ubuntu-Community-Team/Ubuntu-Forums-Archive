---
title: "Very weak wireless signal from the ndiswrapper driver (realtek 8187)"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-11
The wireless signal of my wlan (realtek 8187) is very weak in ubuntu. When my notebook is away from the router more than 3 metres the connection is broken. 

I put my router right beside my notebook and do the ping test  in windows xp and ubuntu for comparison[package size is 64bytes in both os]. The response time in xp is 1ms and 30ms for ubuntu.


Is that because of the low transmission power of the wlan in ubuntu? How can I turn it up? Is there anyway to boost up the signal? Many thanks!



```
 iwconfig
wlan0     IEEE 802.11bg  ESSID:"router"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:45:1a:56:31   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=39/100  Signal level:56/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

coppen@coppen-laptop:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:19:5B:DF:63:DA
                    ESSID:"homerouter269"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=43/100  Signal level:52/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001b23f49179
                    Extra: Last beacon: 8ms ago

coppen@coppen-laptop:~$ 

```


MANY THANKS!

---

