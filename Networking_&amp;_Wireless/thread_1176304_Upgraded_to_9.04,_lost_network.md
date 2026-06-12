---
title: "Upgraded to 9.04, lost network"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2009-06-02
Hey yall. I upgraded to 9.04 through the automatic update/upgrade option on Kubuntu. Went smooth and flawless except one issue: I lost internet/network connectivity. I ran lshw -C network and it spit back the Broadcom BCM4318 card I have, and it states that the driver is in place and working. I believe it is the b43 driver, it is the restricted driver I enabled while using 8.10. I plugged in all my network info, the card is broadcasting and open to receive, I simply can't get a network connection. I set it to connect automatically but it doesn't connect upon power-up/login. The card power on indicator light is illuminated, and Jaunty is recognizing the card being there. I am due to start online courses this week and won't be able to use my wife's machine for it, so internet is much needed on mine. Thanks in advance for any help or advice.

---

### Post by djmoore85 on 2009-06-03
Anybody have any ideas? Starting point or something? I am hardwired through ethernet but I need my comp portable again. Any help or a solution out there?

---

### Post by superprash2003 on 2009-06-04
post output of the following
1)iwconfig
2)sudo iwlist scanning

---

### Post by djmoore85 on 2009-06-04
```
aniel@Danielkubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Kidwell"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated                                                                   
          Tx-Power=20 dBm                                             
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B       
          Power Management:off                                        
          Link Quality:0  Signal level:0  Noise level:0               
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0    
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0    

pan0      no wireless extensions.

daniel@Danielkubuntu:~$ sudo iwlist scanning
[sudo] password for daniel:                 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:F9:16:17
                    ESSID:"Kidwell"           
                    Mode:Master               
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/100  Signal level:-78 dBm  Noise level=-73 dBm                                                               
                    Encryption key:off                                
                    IE: Unknown: 00074B696477656C6C                   
                    IE: Unknown: 010882848B962430486C                 
                    IE: Unknown: 030106                               
                    IE: Unknown: 2A0104                               
                    IE: Unknown: 2F0104                               
                    IE: Unknown: 32040C121860                         
                    IE: Unknown: DD09001018020015000000               
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                                                                    
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                                                                     
                              12 Mb/s; 48 Mb/s                        
                    Extra:tsf=000000035e5da183                        
                    Extra: Last beacon: 12ms ago                      
          Cell 02 - Address: 00:21:29:6B:B0:17                        
                    ESSID:"House of the Risingsun"                    
                    Mode:Master                                       
                    Channel:11                                        
                    Frequency:2.462 GHz (Channel 11)                  
                    Quality=60/100  Signal level:-54 dBm  Noise level=-73 dBm                                                               
                    Encryption key:on                                 
                    IE: Unknown: 0016486F757365206F662074686520526973696E6773756E                                                           
                    IE: Unknown: 010882848B962430486C                 
                    IE: Unknown: 03010B                               
                    IE: Unknown: 2A0104                               
                    IE: Unknown: 2F0104                               
                    IE: Unknown: 32040C121860                         
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483441383236381054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088                                                             
                    IE: Unknown: DD090010180200F4000000               
                    IE: WPA Version 1                                 
                        Group Cipher : CCMP                           
                        Pairwise Ciphers (1) : CCMP                   
                        Authentication Suites (1) : PSK               
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                                                                    
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                                                                     
                              12 Mb/s; 48 Mb/s                        
                    Extra:tsf=000000309143a183                        
                    Extra: Last beacon: 556ms ago                     
          Cell 03 - Address: 00:1D:7E:0B:56:F7                        
                    ESSID:"DanielElise713"                            
                    Mode:Master                                       
                    Channel:11                                        
                    Frequency:2.462 GHz (Channel 11)                  
                    Quality=61/100  Signal level:-52 dBm  Noise level=-73 dBm                                                               
                    Encryption key:on                                 
                    IE: Unknown: 000E44616E69656C456C697365373133     
                    IE: Unknown: 010882848B961224486C                 
                    IE: Unknown: 03010B                               
                    IE: Unknown: 2A0104                               
                    IE: Unknown: 32040C183060                         
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000                                                   
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000                                                           
                    IE: Unknown: 3E0100                               
                    IE: WPA Version 1                                 
                        Group Cipher : TKIP                           
                        Pairwise Ciphers (1) : TKIP                   
                        Authentication Suites (1) : PSK               
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00                                                       
                    IE: Unknown: 7F0101                               
                    IE: Unknown: DD07000C4307000000                   
                    IE: Unknown: 0706555320010B10                     
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000                                           
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000032e00e70c7f
                    Extra: Last beacon: 804ms ago
          Cell 04 - Address: 00:18:F8:F5:23:D8
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/100  Signal level:-81 dBm  Noise level=-73 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000005e7070c4fe
                    Extra: Last beacon: 1148ms ago

pan0      Interface doesn't support scanning.
```

Hopefully this tells ya what you need to know

---

### Post by superprash2003 on 2009-06-08
what happens when you click on the networking icon on the top bar to the right? do you see a dropdown list of available wifi networks??

---

### Post by djmoore85 on 2009-06-12
Which top bar? I only have one panel at the bottom. Running Kubuntu, it didn't come with a top and bottom panel. Unless I goofed up and am supposed to have it. Anybody think of what it might be yet? Still waitin for a fix...

---

