---
title: "Wireless Suddenly Stopped"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Keithodulaigh on 2010-01-23
Hi Everyone,

My internet was working an hour ago but seems to have stopped after installing some updates. I'm using Ubuntu 9.10. I've restarted my router but I know it's working because Windows works. My wlan card is a bcm4318 based card. 

It's able to see my network and lets me enter the WPA key but then it fails. I've trid changing security levels on router and machine to WEP to see if that was a problem but it wasn't.

As I said it was working perfectly about an hour ago...

ifconfig output:

```

eth0      Link encap:Ethernet  HWaddr 00:30:18:aa:65:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6346 (6.3 KB)  TX bytes:6346 (6.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:ec:c5:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1128 (1.1 KB)  TX bytes:10136 (10.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-EC-C5-E7-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Output from iwlist scan:

```

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:57:BC:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"UPC 7 THE GREEN "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f05f7e181
                    Extra: Last beacon: 350ms ago
                    IE: Unknown: 001055504320372054484520475245454E20
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 02 - Address: 00:0F:CC:59:45:BC
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"wlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003981e140
                    Extra: Last beacon: 1070ms ago
                    IE: Unknown: 0004776C616E
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C

pan0      Interface doesn't support scanning.

```

Any ideas appreciated.

---

### Post by Keithodulaigh on 2010-01-23
I did a re-install and it didn't work. Then I moved the antenna on my card a bit and it worked. I'm guessing my antenna might be a bit "dodgy".

Thanks for looking.

---

