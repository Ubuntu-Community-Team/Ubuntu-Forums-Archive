---
title: "Can't find my network, but can find others"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by Kane_Ftw on 2009-02-04
I'm new to Ubuntu, recently installing Ubuntu 8.10 with wubi.

I had trouble getting the wireless to work in the first place, because i didn't have bcm43xx drivers for my Broadcom wireless card. I got my wireless working, and i can see 10 networks in my area, but i can't see mine..

I've googled and all i've found is that supposedly that my SSID isn't being broadcasted, but wouldn't that mean that I wouldn't be able to find my network in windows ?

Post here if you need me to get any information via terminal.

Thanks;)
-Kane_Ftw

---

### Post by Kane_Ftw on 2009-02-04
BUMP - I'm connecting via someone elses unprotected network, and if i want to connect to my network i have to plug a cable from my desktop to a laptop, then bridge the connections on the laptop (WinXP)..
 
If anyone can point me in the right direction if there is anywhere which will tell me how i can fix this, it would be much apreciated.

---

### Post by lucaspr on 2009-02-04
When your SSID is not broadcasted you won´t be able to find it in windows too. 

BUT if you have already registered with the network or 'made a connection' to it it will be able to 'see' your network because it knows its there. (at least this is the only explaination that makes sense to me :))

In Ubuntu try configuring your Wireless network manually.. See if that works!

Can't help you too much, I'm on a cable here :)

---

### Post by Kane_Ftw on 2009-02-04
The SSID must be broadcasting then, and there is no other way i can connect to my wireless network, as my router is too far away..

I have tried manually setting up, and it fails, same if i try connecting to hidden network.

_____________

I read another post by a person with the same issue, the problem wasn't resolved, but they were asked to post;
lspci -nn
lshw -C network
iwlist scan
ifconfig

```

kane@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:0204]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:1204]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:2204]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:3204]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:4204]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:7204]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) [1002:5940] (rev 01)

```

```

kane@ubuntu:~$ su
Password: 
root@ubuntu:/home/kane# lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:04:61:a0:b5:b6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:f5:18:b0:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.9 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:f9:c5:e5:be:dc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@ubuntu:/home/kane# 

```

```

root@ubuntu:/home/kane# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:CE:68:41:BE
                    ESSID:"BTHub-8BB0"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/100  Signal level:-63 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                    Extra:tsf=000004c86e4a466f
                    Extra: Last beacon: 580ms ago
          Cell 02 - Address: 00:18:F6:AF:F9:61
                    ESSID:"BTHomeHub-9168"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=51/100  Signal level:-77 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000f6bb38c4006
                    Extra: Last beacon: 268ms ago
          Cell 03 - Address: 00:14:7F:D4:28:1F
                    ESSID:"BTHomeHub-5677"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=50/100  Signal level:-78 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000003b835d9d004
                    Extra: Last beacon: 268ms ago
          Cell 04 - Address: 00:1F:9F:3D:C2:5D
                    ESSID:"BTHomeHub-BA64"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=45/100  Signal level:-83 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000081df363cd77
                    Extra: Last beacon: 376ms ago
          Cell 05 - Address: 00:01:E3:E8:E7:60
                    ESSID:"OrangeE8E75E"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level:-75 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001806c20b1b8
                    Extra: Last beacon: 84ms ago
          Cell 06 - Address: 00:1B:2F:40:1D:F0
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level:-75 dBm  Noise level=-68 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000e07ec21160
                    Extra: Last beacon: 24ms ago
          Cell 07 - Address: 00:0E:2E:47:AA:94
                    ESSID:"Internet"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level:-75 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002ff9e21e01c
                    Extra: Last beacon: 452ms ago
          Cell 08 - Address: 00:1B:2F:43:9F:54
                    ESSID:"SKY57821"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/100  Signal level:-80 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000087aa1581
                    Extra: Last beacon: 88ms ago
          Cell 09 - Address: 00:18:4D:67:3C:BE
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/100  Signal level:-81 dBm  Noise level=-68 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000bdc86155
                    Extra: Last beacon: 124ms ago

pan0      Interface doesn't support scanning.

```

```

root@ubuntu:/home/kane# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:61:a0:b5:b6  
          inet6 addr: fe80::204:61ff:fea0:b5b6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2660 (2.6 KB)  TX bytes:11835 (11.8 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18585 (18.5 KB)  TX bytes:18585 (18.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:18:b0:19  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe18:b019/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118273895 (118.2 MB)  TX bytes:9981520 (9.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-F5-18-B0-19-30-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/home/kane# 

```

Don't know if that will help get me an answer, but the more info the better i guess :D.

---

### Post by Kane_Ftw on 2009-02-04
BUMP - Don't want this to die :(

---

### Post by Kane_Ftw on 2009-02-04
Bring
Up
Mu
Post

---

### Post by Kane_Ftw on 2009-02-05
Still need help with this.. :(

---

### Post by Coinneach on 2009-02-05
Have you tried to reset your router to default? and if not, check the back of the router and hold in the button for 30 seconds while connected. That's how mine works anyway, give it a try and see if it gets recognized.

---

### Post by Kane_Ftw on 2009-02-06
I'll give that a try that.

The only things I have changed with my router is opening some ports, would that make any difference ?

---

### Post by dxd_2009 on 2009-02-06
to fix it 

go to Bios


1


[http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg](http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg)





2


[http://www.freeimagehosting.net/uploads/a618cee753.jpg](http://www.freeimagehosting.net/uploads/a618cee753.jpg)


Not all Bios are same

---

### Post by Kane_Ftw on 2009-02-07
Thanks for the help everyone, problem resolved.

I had a bit of trouble when i reset, as i couldn't find my ISP infomation, and was stuck without internet for a few hours, but it's all sorted out, and I'm now connected to my network.:D:D:D

---

### Post by Coinneach on 2009-02-07
Glad to hear it! ;)

---

