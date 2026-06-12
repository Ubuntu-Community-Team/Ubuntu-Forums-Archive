---
title: "Wireless connection resets"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by EriktheAwful on 2012-01-28
I've been having daily issues with my wireless connection, running Ubuntu 11.10.  My wife's laptop and my daughter's netbook both connect with no problem and they can stream Netflix with rarely any issues - both running Windows 7.

I have to re-enter my router's password pretty often when I'm surfing the web. I can play Urban Terror for almost exactly 1:50 at a time, then the connection interrupts for about ten seconds. Fortunately it doesn't dump me from the game.

Here's the terminal output from ifconfig, iwconfig, and iwlist scanning. Any ideas?

ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:cd:65:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62248 (62.2 KB)  TX bytes:62248 (62.2 KB)

ra0       Link encap:Ethernet  HWaddr c8:3a:35:ce:20:94  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fece:2094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46938001 (46.9 MB)  TX bytes:342411 (342.4 KB)
          Interrupt:18 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Belkin"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 94:44:52:0F:DF:5F   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-63 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 94:44:52:0F:DF:5F
                    Protocol:802.11b/g/n
                    ESSID:"Belkin"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-61 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

---

### Post by EriktheAwful on 2012-01-29
Found this: [https://bugzilla.redhat.com/show_bug.cgi?id=490493](https://bugzilla.redhat.com/show_bug.cgi?id=490493)

It sounds like my problem, specifically, [https://bugzilla.redhat.com/show_bug.cgi?id=490493#c9](https://bugzilla.redhat.com/show_bug.cgi?id=490493#c9)

Seeing as this was apparently a problem in 2009, was it corrected? Am I barking up the wrong tree?

---

### Post by pmag56 on 2012-02-05
I had the same problem after the intial installation on my Gateway tablet 275, however, I plugged in a "wired connection", downloaded all the updates and it resolved the issue.

I thought this might help 2012 users like me who are new to Ubuntu 11.10.

Pedro

---

### Post by EriktheAwful on 2012-02-15
I'm current on updates. I do have a wireless connection, it just isn't stable. The wireless router and DSL modem are about 30 feet away, and stringing CAT across the floor is not a feasible long-term solution.

Urban Terror was unplayable tonight. My son was playing on the Windows XP machine, directly plugged into the router with no serious lag.

---

### Post by EriktheAwful on 2012-08-25
Never got any answers, still having the same problem. Any new ideas?

Natty Narwhal 11.10, not 11.04, still trying to figure out how to change that on my info.

---

