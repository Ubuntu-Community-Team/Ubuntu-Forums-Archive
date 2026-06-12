---
title: "wlan shown as eth1..."
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by georgew77 on 2009-03-24
Ok I am struggling to get my TX110 laptop wireless working here (broadcom), after a little play it shows the wifi in ifconfig and sudo iwlist scanning, but its identified as eth1 and I cant seem to make it connect to it??

TIA for any help

G.

```

john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:44:85:50  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe44:8550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16443959 (16.4 MB)  TX bytes:775519 (775.5 KB)
          Interrupt:20 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:50:f8:8c  
          inet6 addr: fe80::21a:73ff:fe50:f88c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:115180
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

john@john-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:B2:D6:4E
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-23 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1C:DF:C6:BD:42
                    ESSID:"sweetie1"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-84 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:0F:B5:EA:46:10
                    ESSID:"LED"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-84 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

```

---

### Post by jjpcexpert on 2009-03-24
I have the same "issue" with mapping, and nonetheless I connect to the wlan network WHEN I re-enable the Driver in LM 6 Xfce CE.

---

### Post by georgew77 on 2009-03-24
Yeah I sorted it about 30sec ago - I booted the 4328 driver, and reinstalled the old HP thing (bcmwl5.inf) I used in the past, now its working ok - still called eth1 but it works.

Touchscreen works too which is a winner...


G.

---

