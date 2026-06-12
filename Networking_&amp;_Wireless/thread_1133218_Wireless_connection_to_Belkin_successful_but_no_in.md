---
title: "Wireless connection to Belkin successful but no internet connection"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by patslap on 2009-04-22
I am using 8.10 on a Acer Extensa 5220 laptop with a Broadcom wireless pci card running via ndiswrapper. I has worked well for the last year connecting to a Buffalo router and then onto a cable modem for internet access.

I have moved address and there is an existing Wireless network I am now trying to share. The access point is via a Belkin 54g modem/router (model number F5D7632-4 version 1000uk). Network Manager can see the router and establish a successful connection, however, I am unable to downlaod more than a few k of data from internet. e.g. firefox will download some unformatted text from google homepage, but not images, and then I receive a connection interrupted message if I try and visit other pages, and I cannot use any other web services such as ftp, popmail, smtp, or apt-get.

The other laptop (Toshiba) in the house also runs ubuntu 8.10 and has no connection issues at all. This has been connecting to this same Belkin modem/router for around a year without problems, so I am unsure why my Acer laptop is having them.

If I plug an ethernet cable between Acer laptop and router then internet connection is fine - it is juts wirelessly that internet is unreachable.

Here is the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:4c:01:fc:ac  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe01:fcac/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6176 errors:0 dropped:0 overruns:0 frame:12734
          TX packets:8091 errors:173 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5735033 (5.7 MB)  TX bytes:942216 (942.2 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:72:07:11:03  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe07:1103/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25387350 (25.3 MB)  TX bytes:4943140 (4.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:147693 (147.6 KB)  TX bytes:147693 (147.6 KB)
```

and laspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

and iwconfig:

```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
irda0     no wireless extensions.

pan0      no wireless extensions.

```

and cell showing my router from sudo iwlist eth0 scan:
```
 Cell 01 - Address: 00:12:BF:07:4A:4A
                    ESSID:"netgear"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-33 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```


Can anyone help please?

Many thanks

---

### Post by patslap on 2009-04-23
bump

---

### Post by patslap on 2009-04-24
Anyone?
](*,)

---

### Post by chkneater on 2010-12-02
Sorry, I've been having the same issue ever since I changed addresses.  I was connecting fine to another Belkin router with my Belkin wireless 802.11 usb card and when I moved I started having a hard time connecting to the linksys router that is close by even though I can get a strong signal most times.  I've been searching for a while for an answer. I think I may have found one but I want to test it on my own computer before suggesting it to anyone else.

---

