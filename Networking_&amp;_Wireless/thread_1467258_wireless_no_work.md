---
title: "wireless no work"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by spooli on 2010-04-30
hello

i need help

i have installed ubuntu10.04 my wireles card is detected correctly but i can't connect to wireless :(

```

messi89@messi89-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:97:68:d2:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:20 Adresse de base:0xe400 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:140 erreurs:0 :0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:10960 (10.9 KB) Octets transmis:10960 (10.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:3b:13:8e:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

```
```

messi89@messi89-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Messi89"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


```

messi89@messi89-desktop:~$ /sbin/iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:7E:09:D7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/100  Signal level=23/100  
                    Encryption key:on
                    ESSID:"ABDLMLK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000530d157c9a
                    Extra: Last beacon: 5332ms ago
                    IE: Unknown: 00074142444C4D4C4B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
          Cell 02 - Address: 00:21:63:2A:11:BE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/100  Signal level=24/100  
                    Encryption key:off
                    ESSID:"Messi89"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000eed0404c
                    Extra: Last beacon: 6000ms ago
                    IE: Unknown: 00074D657373693839
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 00:11:3B:0D:02:C8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/100  Signal level=23/100  
                    Encryption key:on
                    ESSID:"zoheir informatique"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000023fa1a82c
                    Extra: Last beacon: 5752ms ago
                    IE: Unknown: 00137A6F6865697220696E666F726D617469717565
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

```

messi89@messi89-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7300 GT] (rev a1)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:02.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
messi89@messi89-desktop:~$
```

```

nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        00:11:3B:13:8E:87

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    zoheir informatique: Infra, 00:11:3B:0D:02:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    Messi89:         Infra, 00:21:63:2A:11:BE, Freq 2412 MHz, Rate 54 Mb/s, Strength 23
    ABDLMLK:         Infra, 00:24:01:7E:09:D7, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:21:97:68:D2:7B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```

any one can help me :(

---

### Post by spooli on 2010-04-30
please help !

---

### Post by mark bower on 2010-04-30
have you left clicked the network manager icon, upper rt corner of screen.  see your AP (SSID), select it, and you should be connected.

mark

---

### Post by spooli on 2010-04-30
> **mark bower said:**
> have you left clicked the network manager icon, upper rt corner of screen.  see your AP (SSID), select it, and you should be connected.

mark

yes when i select my ap nm start searching but after 10 ~ 30s no connection !

---

