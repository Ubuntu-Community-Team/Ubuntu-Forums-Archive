---
title: "Wireless is working, can't connect to my router"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by nelstomlinson on 2012-02-26
My wireless is working, but it can't connect to my router.
ifconfig shows:

ra0       Link encap:Ethernet  HWaddr 74:de:2b:db:ef:ec  
          inet6 addr: fe80::76de:2bff:fedb:efec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:704877 (704.8 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

iwlist scan finds my wireless network:
ra0       Scan completed :
          Cell 01 - Address: 00:23:69:2E:AD:51
                    Protocol:802.11b/g
                    ESSID:"Tomlinson Family Private"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=89/100  Signal level=-55 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

I can't find anything that will let me connect.  I've tried the nm-applet, which doesn't seem to find my network, and wifi-radar, which  can find my network, but can't connect.

Does anyone have any ideas on how to troubleshoot this?

---

### Post by gordintoronto on 2012-02-26
Yes, change the SSID to "family" (no upper case or spaces).

Having an SSID which identifies the owner is seldom a good idea.

If you are still unable to connect, tell us a few things: whether you have ever connected a Ubuntu computer to a wireless network, what version of Ubuntu you are using, step-by-step how you are trying to connect.

---

