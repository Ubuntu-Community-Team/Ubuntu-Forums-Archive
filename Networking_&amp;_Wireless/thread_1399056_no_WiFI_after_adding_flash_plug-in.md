---
title: "no WiFI after adding flash plug-in"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by PecaBa on 2010-02-05
I have just installed Ubuntu 9.10, and wireless internet connection was working fine. Using that connection I installed adobe flash plug-in. A huge list of packages was added automatically. 
After first reboot, I am not able to establish wireless internet connection. I set wlan0 to "Managed mode", and scan reports to me "Master mode". What's wrong, any idea? 

Here is additional info:


>iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"SpeedTouch988D11"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


>iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:68:BA:D6:89
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouch988D11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000effaeacda0
                    Extra: Last beacon: 2136ms ago
                    IE: Unknown: 00105370656564546F756368393131443130
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

---

