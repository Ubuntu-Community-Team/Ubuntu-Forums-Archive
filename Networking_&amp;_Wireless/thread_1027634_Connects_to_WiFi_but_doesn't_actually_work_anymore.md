---
title: "Connects to WiFi but doesn't actually work anymore."
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Mike_SMD on 2009-01-01
As of today I've got a strange new problem, originally I had a heck of a time setting up wifi with my laptop. I had to use NDIS Wrapper as it's an HP with the unfriendly Broadcom card... however... It's been working just fine for months though.

Now, it looks like things are connecting as usual with great signal strength but I can't actually use the internet. Nothing but timeouts and connectivity errors with Firefox etc.

The hardwired connection works fine.

Does anyone have any advice as to where/how to begin troubleshooting this bug?

---

### Post by melojo on 2009-01-01
open a terminal and post the output of

```
ifconfig
```
and
```
iwlist scan
```

this will give us more info so someone can help.

---

### Post by Mike_SMD on 2009-01-01
Hi, thanks for taking the time to help out.
Here's the information that you asked for, it's essentially three flavours of greek to me but I hope it helps narrow things down.

I really appreciate the help!

Mike.

--
-- 

wendy@wendy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:fc:e1:c5  
          inet6 addr: fe80::21b:24ff:fefc:e1c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:324 (324.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10700 (10.4 KB)  TX bytes:10700 (10.4 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1a:73:fa:18:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:529269 (516.8 KB)  TX bytes:9806 (9.5 KB)
          Interrupt:19 Memory:f6000000-f6004000 

wendy@wendy-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:40:F4:FD:75:32
                    ESSID:"mike's place"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:40:05:BD:0B:2F
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1B:11:61:9D:E5
                    ESSID:"Lodge"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

wendy@wendy-laptop:~$

---

### Post by Mike_SMD on 2009-01-02
So...
Solved!

But I don't know why.

Anyway, I got creative and opened up a connection to my router, reset all the information for wireless access and it now works.

I'm assuming that means it was some kind of hardware glitch.

The problem has been corrected even if I know nothing more concerning the cause.

Thanks to everyone who took a look and gave it a ponder with me!

Mike.

---

