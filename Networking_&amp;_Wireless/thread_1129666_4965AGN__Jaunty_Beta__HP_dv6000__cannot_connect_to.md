---
title: "4965AGN / Jaunty Beta / HP dv6000 / cannot connect to specific router"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by Merritt.kr on 2009-04-18
I have an HP dv6000 series laptop (specifically dv6663ca). It has the Intel 4965AG(N) wireless adapter. I am currently running Jaunty Beta. Cannot connect to Linksys WRT54GL v1.1 router.

The laptop cannot connect to my wireless router at home. It *can* connect to the wireless router at work (With WEP). I had WPA2 on my router, tried changing it to WPA, WEP, and unsecured. I attempt to connect, it starts handshaking, and after approx. 2 minutes fails with no error.

**My routers logs report:**
```
Apr 18 21:46:06 unknown daemon.info dnsmasq[7143]: DHCPDISCOVER(br0) 00:13:e8:b7:42:c1 
Apr 18 21:46:06 unknown daemon.info dnsmasq[7143]: DHCPOFFER(br0) 192.168.1.109 00:13:e8:b7:42:c1 
Apr 18 21:46:11 unknown daemon.info dnsmasq[7143]: DHCPDISCOVER(br0) 00:13:e8:b7:42:c1 
Apr 18 21:46:11 unknown daemon.info dnsmasq[7143]: DHCPOFFER(br0) 192.168.1.109 00:13:e8:b7:42:c1 
Apr 18 21:46:22 unknown daemon.info dnsmasq[7143]: DHCPDISCOVER(br0) 00:13:e8:b7:42:c1 
Apr 18 21:46:22 unknown daemon.info dnsmasq[7143]: DHCPOFFER(br0) 192.168.1.109 00:13:e8:b7:42:c1
```

**lspci**
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

**sudo lshw -C network** reports that driver for wifi is iwlagn

**dmesg**
```
[ 2786.883849] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2787.080231] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2787.280200] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2787.480184] wlan0: authentication with AP f624e6b8 timed out                                                                                                  
[ 2808.681692] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2808.696434] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2808.896113] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2808.902058] wlan0: authenticated                                                                                                                              
[ 2808.902067] wlan0: associate with AP f624e6b8                                                                                                                 
[ 2808.904833] wlan0: RX AssocResp from f46c804e (capab=0x411 status=0 aid=1)                                                                                    
[ 2808.904840] wlan0: associated                                                                                                                                 
[ 2881.531025] wlan0: deauthenticated (Reason: 7)                                                                                                                
[ 2881.540406] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2881.558584] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2881.756185] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2881.762179] wlan0: authenticated                                                                                                                              
[ 2881.762186] wlan0: associate with AP f624e6b8                                                                                                                 
[ 2881.764673] wlan0: RX AssocResp from f47c404e (capab=0x411 status=0 aid=1)                                                                                    
[ 2881.764680] wlan0: associated                                                                                                                                 
[ 2926.884588] wlan0: direct probe to AP f624e6b8 try 1                                                                                                          
[ 2926.886644] wlan0 direct probe responded                                                                                                                      
[ 2926.886651] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2927.084184] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2927.284201] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2927.484184] wlan0: authentication with AP f624e6b8 timed out                                                                                                  
[ 2985.877622] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2985.888957] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 2985.888995] wlan0: authenticated                                                                                                                              
[ 2985.889000] wlan0: associate with AP f624e6b8                                                                                                                 
[ 2985.893225] wlan0: RX AssocResp from f47e004e (capab=0x411 status=0 aid=1)                                                                                    
[ 2985.893231] wlan0: associated                                                                                                                                 
[ 3045.536548] wlan0: disassociating by local choice (reason=3)                                                                                                  
[ 3054.088645] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 3054.108124] wlan0: authenticate with AP f624e6b8                                                                                                              
[ 3054.108172] wlan0: authenticated                                                                                                                              
[ 3054.108177] wlan0: associate with AP f624e6b8
[ 3054.113219] wlan0: RX ReassocResp from f465404e (capab=0x411 status=0 aid=1)
[ 3054.113227] wlan0: associated
[ 3132.539305] wlan0: deauthenticated (Reason: 7)
[ 3158.846483] wlan0: authenticate with AP f624e6b8
[ 3158.865802] wlan0: authenticate with AP f624e6b8
[ 3158.865850] wlan0: authenticated
[ 3158.865855] wlan0: associate with AP f624e6b8
[ 3158.869837] wlan0: RX AssocResp from f3c6c04e (capab=0x411 status=0 aid=1)
[ 3158.869844] wlan0: associated
[ 3176.962857] wlan0: beacon loss from AP f624e6b8 - sending probe request
[ 3217.528286] wlan0: disassociating by local choice (reason=3)
[ 3226.023322] wlan0: authenticate with AP f624e6b8
[ 3226.046744] wlan0: authenticate with AP f624e6b8
[ 3226.052877] wlan0: authenticated
[ 3226.052885] wlan0: associate with AP f624e6b8
[ 3226.055337] wlan0: RX ReassocResp from f3c9004e (capab=0x411 status=0 aid=1)
[ 3226.055343] wlan0: associated
[ 3296.978007] wlan0: deauthenticated (Reason: 7)
[ 3158.846483] wlan0: authenticate with AP f624e6b8
[ 3158.865802] wlan0: authenticate with AP f624e6b8
[ 3158.865850] wlan0: authenticated
[ 3158.865855] wlan0: associate with AP f623e6b8
[ 3158.869837] wlan0: RX AssocResp from f3c6c04e (capab=0x411 status=0 aid=1)
```

I'm sorry if any of these outputs are too short, I am posting on my desktop system since the notebook does not have wireless. If you need more detail I will be happy to provide it.

**Edit:**
I forgot to mention that as a troubleshooting step, I installed linux-backports-modules-jaunty, with no effect.

---

### Post by superprash2003 on 2009-04-19
post output of the following commands when your at home
1)ifconfig
2)iwconfig
3)sudo iwlist scanning

---

### Post by Merritt.kr on 2009-04-19
**ifconfig**:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:ae:f2:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              
          Interrupt:250 Base address:0x4000                   

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:b7:42:c1
          inet6 addr: fe80::213:e8ff:feb7:42c1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:488 (488.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-B7-42-C1-32-63-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```



**iwconfig**:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Ein"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Tx-Power=14 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```



**sudo iwlist scanning**:

```
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:7A:5D:D3
                    Channel:9                 
                    Frequency:2.452 GHz (Channel 9)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on                    
                    ESSID:"Ein"                          
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s                 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s          
                    Mode:Master                                         
                    Extra:tsf=00000003d73d6183                          
                    Extra: Last beacon: 96ms ago                        
                    IE: Unknown: 000345696E                             
                    IE: Unknown: 010882848B962430486C                   
                    IE: Unknown: 030109                                 
                    IE: Unknown: 2A0104                                 
                    IE: Unknown: 2F0104                                 
                    IE: IEEE 802.11i/WPA2 Version 1                     
                        Group Cipher : TKIP                             
                        Pairwise Ciphers (2) : CCMP TKIP                
                        Authentication Suites (1) : PSK                 
                    IE: Unknown: 32040C121860                           
                    IE: Unknown: DD06001018020003                       
          Cell 02 - Address: 00:1C:10:49:CD:10                          
                    Channel:6                                           
                    Frequency:2.437 GHz (Channel 6)                     
                    Quality=25/70  Signal level=-85 dBm                 
                    Encryption key:on                                   
                    ESSID:""                                            
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s                 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s          
                    Mode:Master                                         
                    Extra:tsf=0000007cd5dc8185                          
                    Extra: Last beacon: 2988ms ago                      
                    IE: Unknown: 000700000000000000                     
                    IE: Unknown: 010882848B962430486C                   
                    IE: Unknown: 030106                                 
                    IE: Unknown: 0504FF010000                           
                    IE: Unknown: 2A0104                                 
                    IE: Unknown: 2F0104                                 
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606051300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051300000000000000000000000000000000000000

pan0      Interface doesn't support scanning.
```

---

### Post by StuartN on 2009-04-19
Is your router one of the two listed, "Ein" or the one without a broadcast SSID?

---

### Post by Merritt.kr on 2009-04-19
Yes, my router is the one with the SSID "Ein". (from Cowboy Bebop, for anyone curious.)

---

### Post by benvantende on 2009-04-20
Hey,

I am having the same problems. I can't connect to any secure network. I am not in the position to change my router, because it is a company router. I would have expected some solution somewhere. Strangely enough I can't find that anywhere. I am using 4965AGN/Jaunty RC/HP dv9000.

---

### Post by superprash2003 on 2009-04-22
in your terminal type **sudo dhclient wlan0** and post output

---

### Post by Merritt.kr on 2009-04-22
**sudo dhclient wlan0**

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:13:e8:b7:42:c1
Sending on   LPF/wlan0/00:13:e8:b7:42:c1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by superprash2003 on 2009-05-08
your machine seems to be able to connect fine. Its just that it isnt getting an ip address. Does this router give other machines an ip address via DHCP?? another alternative is to try static ip..[http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

