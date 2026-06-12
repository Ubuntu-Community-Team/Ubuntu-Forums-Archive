---
title: "Internet slower than windows at home"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by kurt0375 on 2012-09-25
Hi
please excuse me i am completely new to Ubuntu/Linux and have had little/no experience in the past, although this is now hopefully all to change.

I installed Ubuntu on to my laptop yesterday at uni (as i am trying to learn CLI and a new os) using their wireless  Internet connection and the intern speed was as quick as my windows7 speed. When i got home last night i set it up on my home network and booted Ubuntu and the Internet was extremely slow. I put this down to maybe maintenance with the ISP or something on the line. this morning i booted windows did what i needed to do and the Internet was perfect, then restarted and booted Ubuntu and again the Internet was slow. 

Please help
Thank You

---

### Post by TenPlus1 on 2012-09-25
It could be a router issue, check the settings within your router's configuration page (check manual for this) and see what's active, some settings can slow down Ubuntu...

---

### Post by paulocr on 2012-09-25
can you try using a wired connection? that would narrow it down to the wireless card or not.

---

### Post by kurt0375 on 2012-09-25
> **paulocr said:**
> can you try using a wired connection? that would narrow it down to the wireless card or not.

Just tried a wired connection and worked perfectly. But still no luck wirelessly

---

### Post by paulocr on 2012-09-25
Type this in a terminal and paste the results here:

sudo lshw -C network

---

### Post by kurt0375 on 2012-09-25
> **paulocr said:**
> Type this in a terminal and paste the results here:

sudo lshw -C network

The wired Results:

```
[sudo] password for kurt: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:6b:89:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c3200000-c320ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: c0
       serial: e8:9a:8f:fb:83:ce
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:49 memory:c3100000-c313ffff ioport:2000(size=128)
```

Wireless Results:

kurt@ubuntu:~$ sudo lshw -C network
  ```
kurt@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:6b:89:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c3200000-c320ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: c0
       serial: e8:9a:8f:fb:83:ce
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:49 memory:c3100000-c313ffff ioport:2000(size=128)

```

---

### Post by paulocr on 2012-09-25
Both your interfaces seem to have the proper configuration and driver running.
What about this one:

cat /etc/resolv.conf

I'd suggest you also take a look at disabling ipv6 which in some cases is the cause of this, you can find some steps here (for 12.04) [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

---

### Post by funicorn on 2012-09-25
The reason is simple, the wifi driver under linux is not good as that in windows.

---

### Post by paulocr on 2012-09-25
> **funicorn said:**
> The reason is simple, the wifi driver under linux is not good as that in windows.

really bad answer..I have never experienced any issues with my installation however the problem described in this post is very common and simple to fix. A simple google search will demonstrate a lot of people with the exact problem and a number of different solutions *not* involving the wifi driver.

---

### Post by uncaspi on 2012-09-25
From terminal type ifconfig to determine the logical name of your wifi card.
Mine is wlan0

Then type sudo iwlist wlan0 scanning

and look for the signal strenght.All below -70 db is good.

Try to increase txpower to 20. And alset set the rate to highest possible.

sudo iwconfig wlan0 rate 54 txpower 20



I don`t think it has something to do with ipv6 since cable speed is ok.

---

### Post by kurt0375 on 2012-09-25
```
kurt@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

what i don't understand is it works at university but not at home, unless when i log into the university wireless it must automatically gets the correct settings. to me the nameserver isn't right surely there should be more ips?

---

### Post by uncaspi on 2012-09-25
It could have to do with the isp nameserver. Also try to swith off power save mode on the card.

sudo iwconfig wlan0 power off











127.0.0.1 is also in my /etc/resolv.conf file so this is not the right place to put the nameserver ip. Look in the application menu for something reltatet to network manager.

---

### Post by kurt0375 on 2012-09-25
> **uncaspi said:**
> From terminal type ifconfig to determine the logical name of your wifi card.
Mine is wlan0

Then type sudo iwlist wlan0 scanning

and look for the signal strenght.All below -70 db is good.

Try to increase txpower to 20. And alset set the rate to highest possible.

sudo iwconfig wlan0 rate 54 txpower 20



I don`t think it has something to do with ipv6 since cable speed is ok.

ifconfig Returned
```
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:fb:83:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:49 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26215 (26.2 KB)  TX bytes:26215 (26.2 KB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:6b:89:63  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fe6b:8963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1293625 (1.2 MB)  TX bytes:242973 (242.9 KB)

```

sudo iwlist wlan0 scanning RETURNED
```
wlan0     Scan completed :
          Cell 01 - Address: 04:C0:6F:3C:B9:A0
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TheMoneys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000019b9db57e
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 00095468654D6F6E657973
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C338E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409050700000000000000000000000000000000000000
          Cell 02 - Address: 02:24:17:CD:A0:C4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040023b0185
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 03 - Address: 02:24:17:CD:A0:C5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040023b07c8
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:FE:F4:2A:D2:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-76JW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a697205611
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 000B4254487562332D37364A57
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: 02:FE:F4:2A:D2:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a697214c9c
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: 12:FE:F4:2A:D2:28
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a697215808
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 00:26:44:1D:C2:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"O2wireless274869"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000026e1de3c59
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 00104F32776972656C657373323734383639
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
          Cell 08 - Address: 00:22:3F:C6:C7:C6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NikeNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005168744183
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 00074E696B654E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: E0:46:9A:05:27:36
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Orangebf9b63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014006f0e180
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 000C4F72616E6765626639623633
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0800000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: 02:01:3B:AB:A8:42
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014fa846ad80
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 11 - Address: 00:01:3B:AB:A8:42
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-PC89"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014fa8432634
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 000B4254487562332D50433839
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 12 - Address: 12:01:3B:AB:A8:42
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014fa8458180
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
```
txpower 20 returned 
```
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument
```

and sudo iwconfig wlan0 rate 54 txpower 20 Returned nothing

---

### Post by kurt0375 on 2012-09-25
> **uncaspi said:**
> It could have to do with the isp nameserver. Also try to swith off power save mode on the card.

sudo iwconfig wlan0 power off


```
kurt@ubuntu:~$ sudo iwconfig wlan0 power off
kurt@ubuntu:~$

```

---

### Post by kurt0375 on 2012-09-27
Tried it again today at University and it works perfectly. Should I try Re-installing Ubuntu?

---

### Post by paulocr on 2012-09-27
I don't think reinstalling is necessary, can you try adding DNS servers manually in the network manager?

You can use Google's DNS 8.8.8.8 and 8.8.4.4

You'll have to switch the "Method" to "Automatic (DHCP) addresses only" before you're able to edit the DNS servers.

---

### Post by kurt0375 on 2012-09-27
I shall try this when i get home is it is fairly pointless trying it at uni where i know the Internet works, is there anyway I can use the same DNS servers that windows uses when connecting to the Internet?

---

### Post by paulocr on 2012-09-27
Sure. Just go into windows and do "ipconfig /all" in DOS command line to find out what they are.

---

### Post by kurt0375 on 2012-09-27
also should i also enter in googles IPv6 DNS servers aswell?

---

### Post by paulocr on 2012-09-27
Just IPv4

---

### Post by gromacs on 2012-09-27
> **paulocr said:**
> Type this in a terminal and paste the results here:

sudo lshw -C network
Hey, I'm having a similar problem where the file transfers to/from Windows Server using samba and cifs (not sure if that's technically correct) is around 500kB/s, while from Windows 7 it's 5mB/s. Could you please take a look, and let me know if anything looks off, or how this output can be interpreted? Thanks
```
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:8e:9d:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic firmware=N/A ip=172.16.3.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0400000-f040ffff

```

I decided to take a closer look at this output, and it appears to me that OP and I have very similar wireless network adapters lol. I suppose that my driver version is correct, so I went ahead and ran the second command that paulocr suggested:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search gromacs.local

```
I know that the DNS on my network is actually 172.16.2.1, in case that's relevant here... The notebook is stationary so signal strength is a constant variable.

---

