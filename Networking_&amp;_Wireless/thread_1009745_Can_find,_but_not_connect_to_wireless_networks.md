---
title: "Can find, but not connect to wireless networks"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by macho on 2008-12-13
I recently installed ndiswrapper for my supported [Airlink 101 AWLH3028]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#PCI") card, and blacklisted the r8180 module as instructed.

It seemed to go fine, and several wireless networks in range show up when I click the double-monitor icon on my Gnome taskbar.  However, when I try to connect to the network, I am asked for the passphrase, it pauses for about ten seconds, then asks me for the passphrase again, and continues on and like this forever, always failing to connect.  It does not give any kind of "password incorrect" message, and I'm quite sure I'm entering the password correctly.

I've tried WEP/WPA/WPA2/no encryption, mostly with the same results.  Turning off encryption seems to allow me to connect (but I'm not, of course, excited about that as a solution), and I was briefly successful connecting to WPA once, but I haven't been able to replicate it.

Any suggestions or thoughts are appreciated.

I am running ubuntu 8.04.1 on an AMD64.  here's some output:

```
$ iwlist wlan1 scan
wlan1     Scan completed :
          Cell 01 - Address: 00:1C:F0:43:7F:72
                    ESSID:"<my_essid>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

```
$ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:21:2f:00:57:9d  
          inet6 addr: fe80::221:2fff:fe00:579d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:487 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:324297 (316.6 KB)  TX bytes:64221 (62.7 KB)
          Interrupt:20 Memory:dffffc00-dffffc25
```

if i run iwevent while trying to connect, it seems to roughly repeat a sequence something like this:
```
22:36:01.386030   wlan1    Set Encryption key:off
22:36:08.470315   wlan1    Set Mode:Managed
22:36:11.799286   wlan1    Set Frequency:2.437 GHz (Channel 6)
22:36:11.799379   wlan1    Set ESSID:"<my_essid>"
22:36:18.975204   wlan1    Association Request IEs:<long_hex_string>
22:36:18.975350   wlan1    Association Response IEs:<shorter_hex_string>
22:36:18.975377   wlan1    New Access Point/Cell address:00:1C:F0:43:7F:72
22:36:22.882714   wlan1    New Access Point/Cell address:Not-Associated
```

---

