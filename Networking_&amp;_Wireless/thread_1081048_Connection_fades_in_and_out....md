---
title: "Connection fades in and out..."
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by zrockstar on 2009-02-26
Installed Wubi today, and after many hours of switching networking cards and routers, I finally found a set up that would work. The wireless network connects at 100%, and I can get downloads up to 1MB a second, but it seems like it fades in and out. When I am doing updates or apt-get, or even surfing the web, I will lose connection for a few seconds, and then it will come back on. Funny thing is though is that the wireless level stays at 100%. Anyone seen this before?

---

### Post by jeremyjjbrown on 2009-02-26
Do you know what wireless card you are using? And what sort of encryption if any?

Find you wireless card with these commands in the terminal "lspci" and "lsusb". You will find it's name on one of those lists and you can search for detailed help in the forums. Chances are someones already posted the solution. If you need help understanding the results of the lspci and lsusb lists post them in a reply.

---

### Post by Kevbert on 2009-02-26
What's the output of
```
iwconfig
``` when connected ? (you may need to do this a few times).
It may be that even though your signal strength is 100% you may have problems with interference or signal quality.  How close is the signal source ? (router ?)  It may even be that the card is receiving too much signal (try moving it away from the source).

---

### Post by superprash2003 on 2009-02-26
also post output of **ifconfig**

---

### Post by zrockstar on 2009-02-26
Thanks for helping guys...

```
jeff@ubuntu:~$ iwconfig

[CODE]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:166
          Rx invalid nwid:0  invalid crypt:617  invalid misc:0

pan0      no wireless extensions.

```

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:52:1b:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1b:2f:61:22:33  
          inet addr:192.168.0.153  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe61:2233/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76754 errors:0 dropped:0 overruns:0 frame:52715
          TX packets:58004 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99733792 (99.7 MB)  TX bytes:7872499 (7.8 MB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 [/CODE]

Wireless card is a Netgear WN311B, connecting to a D-Link router.

---

### Post by thesoothsayer on 2009-02-26
Have you tried scanning the channel to see if any other networks are using the same channel as you?

And have to agree with Kevbert, try moving your router or your laptop's position and see if that helps.

---

### Post by Kevbert on 2009-02-27
How did you install the firmware drivers ? Automatically or via ndiswrapper ?
As thesoothsayer suggests, can you see many other wireless networks ? You can see this by left-clicking on the signal strength icon in the top right-hand corner of your desktop (looks like a set of steps when you are connected).  It's probable that you are using the same channel as other networks, so may need to change channels.
The other thing is are you using any encryption on the network ? You should be using as least WPA, WEP is not so good. It could be that someone else is using your network if you have no encryption running.

---

### Post by superprash2003 on 2009-02-27
post output of **sudo iwlist scanning**

---

### Post by zrockstar on 2009-03-03
Thanks for all the help on this. I know that it is not the distance from the router for sure. There is no way that can be the problem. As far as the drivers, I used the generic driver that Ubuntu downloaded at the first login. Also, this is the only machine having this problem, so I don't think network channel would have anything to do with it. Here is the requested output, once again thanks for the help.

```
jeff@ubuntu:~/depot$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:CF:91:D1
                    ESSID:"Protected Network"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-50 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1F:33:24:92:7D
                    ESSID:"ZACNET"
                    Mode:Managed
                    Frequency=2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD730050F204104A0001101044000102103B000103104700103FD3C2F9B36AA2CA31ED0008BCC1C4D1102100074E45544745415210230007574E523335303010240007574E52333530301042000A313233343536373839301054000800060050F204000110110007574E5233353030100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:14:6C:43:23:70
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:15:05:D0:F5:5E
                    ESSID:"ACTIONTEC"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:15:05:27:3A:33
                    ESSID:"a.beam.reach"
                    Mode:Managed
                    Frequency=2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-84 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:1E:C7:BC:80:01
                    ESSID:"2WIRE354"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

```

---

### Post by superprash2003 on 2009-03-26
your card is able to view networks so thats good.. could you post output of **sudo iwconfig ** again

---

