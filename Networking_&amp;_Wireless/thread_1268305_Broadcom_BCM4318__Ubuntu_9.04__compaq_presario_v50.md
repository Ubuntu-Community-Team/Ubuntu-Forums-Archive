---
title: "Broadcom BCM4318  /Ubuntu 9.04 / compaq presario v5000 laptop: Help please"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by azure03 on 2009-09-16
Hello, I am having a hard time getting the wireless internet to work on my laptop. After installing ubuntu 9.04 my wired and wireless connections would not work. I finally got the wired to work and eventually got the wifi button to turn it on/off to work also, i keep it turned on. If someone can read the information below and give me some suggestions i would greatly appeciate it. Thanks.

Also, I will check back on this post all evening so if anyone needs anymore info I will post it as quickly as possible, thanks again.

**lspci**

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

**lsusb**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**iwconfig wlan0**

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**iwlist scan** **wlan0**

wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:48:71:37
                    ESSID:"home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

---

### Post by azure03 on 2009-09-16
I am trying to connect to a Belkin wireless N router, with WPA-Personal(PSK)

---

### Post by azure03 on 2009-09-17
Nevermind, im going back to windows xp. Ubuntu was pretty cool though while it lasted, except for the no internet part.

---

### Post by Herukam on 2009-10-22
> **azure03 said:**
> Nevermind, im going back to windows xp. Ubuntu was pretty cool though while it lasted, except for the no internet part.

Aww. That's too bad. You will miss a lot. I started to use Ubuntu 3 days ago and I'm loving it. :)

This one worked for me in this problem [http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318)

---

### Post by sgx100 on 2009-10-22
hi,

can u connect to the wireless network
if not try enabling the restricted drivers from system>administration>hardware drivers

Also, I just was able to use wireless on 9.04 on a broadcom 4312 rev 1 by enabling the restricted drivers
I think u shd not have much of a trouble

---

### Post by dheerajrav on 2009-10-31
Try

>>> sudo apt-get install bmcwl-kernel-source

and reboot.

Wifi was recognised and it worked as a charm

---

