---
title: "Thinkpad wireless nic not working in 10.10"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by Gutsanglory on 2011-02-25
Hi all,

I'm kind of a newbie, but am willing to do what it takes to get my wireless back up and working. 
It used to work fine under 10.4
My laptop is a IBM Thinkpad T42, that uses Intel wired and wireless nics. **[COLOR=Red](correction, looks like the wireless nic is actually Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) )[/COLOR]**


-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

-Laptop:~$ dmesg | grep Intel
[    1.260556] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.260560] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.549817] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   17.559856] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   18.758278] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   18.758324] Intel ICH 0000:00:1f.5: setting latency timer to 64

-Laptop:~$ dmesg | grep intel
[   17.083765] intel_rng: FWH not detected
[   17.559856] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   17.741805] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   18.807078] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   18.807098] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   19.684598] intel8x0_measure_ac97_clock: measured 55970 usecs (2696 samples)
[   19.684603] intel8x0: clocking to 48000

If there is anything else you need to see to help diagnose and get this wireless working, let me know.

Thanks in advance,
Guts

---

### Post by walt.smith1960 on 2011-02-25
It looks like your wireless is Atheros

02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

It's curious that it's labeled an Ethernet controller.  WiFi devices seem to usually labeled "Network controller".  You might try dmesg with Atheros,  I'd expect to see something with ath5k_pci or possibly ath9K_pci which is probably not right.  I'm afraid I'm not much help beyond that. Does the command "iwconfig" show anything?

---

### Post by Gutsanglory on 2011-02-25
Checked:

-Laptop:~$ dmesg | grep Atheros
[   19.652457] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)


-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:ce:01:90  
          inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fece:190/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34759934 (34.7 MB)  TX bytes:2174563 (2.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:d7:2b:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

-Laptop:~$ dmesg | grep ath5k
[   18.289604] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.289665] ath5k 0000:02:02.0: registered as 'phy0'
[   19.652428] Registered led device: ath5k-phy0::rx
[   19.652452] Registered led device: ath5k-phy0::tx
[   19.652457] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[   19.652460] ath5k phy0: RF5112B multiband radio found (0x36)

---

### Post by chili555 on 2011-02-25
Let's see if the hardware switch is on:```
rfkill list all
```Also, let's see if there are any interesting kernel messages:```
dmesg | grep ath
```Last, Network Manager will disallow a wireless connection if wired is available. If you disconnect the ethernet cable and click the Network Manager icon, does it show networks? Can you connect?

---

### Post by Gutsanglory on 2011-02-25
Checked:

-Laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
-Laptop:~$ dmesg | grep ath
[    0.383758] device-mapper: multipath: version 1.1.1 loaded
[    0.383763] device-mapper: multipath round-robin: version 1.0.0 loaded
[   18.289604] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.289665] ath5k 0000:02:02.0: registered as 'phy0'
[   19.603354] ath: EEPROM regdomain: 0x66
[   19.603359] ath: EEPROM indicates we should expect a direct regpair map
[   19.603364] ath: Country alpha2 being used: 00
[   19.603367] ath: Regpair used: 0x66
[   19.652428] Registered led device: ath5k-phy0::rx
[   19.652452] Registered led device: ath5k-phy0::tx
[   19.652457] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[   19.652460] ath5k phy0: RF5112B multiband radio found (0x36)

I checked the wireless without the wired connection plugged in, it made no difference. Also within the network manager, under the wireless tab, it lists no wireless adapters at all. On a good note, the physical "Fn" button to enable and disable the wireless card does work, and the wireless is check marked as active in the network manager, but without a supported or found wireless adapter, its not working...... driver issue?

---

### Post by chili555 on 2011-02-25
> but without a supported or found wireless adapter, its not working.Your wireless adapter is found, is supported and has a driver. What does this tell us?```
sudo iwlist wlan0 scan
```Your other readings look just fine.

---

### Post by Gutsanglory on 2011-02-25
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:4A:57:0C:90
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption keyn
                    ESSID:"IBM"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002c04bc18044
                    Extra: Last beacon: 2880ms ago
                    IE: Unknown: 000349424D
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0712434149240414340414640514840314950414
                    IE: Unknown: 200103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 851E000089000F00FF0319003161632D61702D30366100000000000000000026
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1E:4A:54:8C:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption keyn
                    ESSID:"IBM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002c04bb8218c
                    Extra: Last beacon: 3456ms ago
                    IE: Unknown: 000349424D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706434149010B1A
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E030089000F00FF0319003161632D61702D30366100000000000001000027
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101810003A4000027A400004243BC0062326600
          Cell 03 - Address: 00:07:85:B3:31:8E
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption keyn
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00001651b137f19e
                    Extra: Last beacon: 3308ms ago
                    IE: Unknown: 0009000000000000000000
                    IE: Unknown: 010482040B16
                    IE: Unknown: 030104
                    IE: Unknown: 050401020000
          Cell 04 - Address: 00:22:2D:6B:93:89
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption keyn
                    ESSID:"Coolbeans"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e200243cee
                    Extra: Last beacon: 2940ms ago
                    IE: Unknown: 0009436F6F6C6265616E73
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050B0022127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
          Cell 05 - Address: 00:24:01:28:57:4C
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption keyn
                    ESSID:"Inet-Test-8S"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009ea94c07bba
                    Extra: Last beacon: 3164ms ago
                    IE: Unknown: 000C496E65742D546573742D3853
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160700190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340700010000000F000000000000000000000000000000
                    IE: Unknown: DD880050F204104A0001101044000102103B0001031047001098615F70627E3A7598966A21ACE424DA1021000E442D4C696E6B2053797374656D73102300074449522D383235102400024131104200046E6F6E651054000800060050F20400011011001B587472656D65204E2044554F204749474142495420526F75746572100800020084103C000102
          Cell 06 - Address: 00:24:6C:B3:E6:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption keyn
                    ESSID:"TeamPlayer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000066279180
                    Extra: Last beacon: 3588ms ago
                    IE: Unknown: 000A5465616D506C61796572
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010019000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010019000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:0A:F4:2D:8D:3E
                    Channel:64
                    Frequency:5.32 GHz (Channel 64)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001651a0a43049
                    Extra: Last beacon: 2092ms ago
                    IE: Unknown: 0009000000000000000000
                    IE: Unknown: 01088C1218243048606C
                    IE: Unknown: 050401020000
                    IE: Unknown: 851E000084210700FF031100495042422D372D52495345522D524F4F00000023
          Cell 08 - Address: 00:22:2D:CA:18:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Eng-Svr-8NE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a83af9a4d
                    Extra: Last beacon: 2944ms ago
                    IE: Unknown: 000B456E672D5376722D384E45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001F127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
          Cell 09 - Address: 00:22:2D:6E:1F:61
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"Inet-Test-8-NNW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c226df31a2
                    Extra: Last beacon: 3460ms ago
                    IE: Unknown: 000F496E65742D546573742D382D4E4E57
                    IE: Unknown: 010802040B161224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: 00:22:2D:5A:64:A5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:on
                    ESSID:"5A649D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000003bc4af142
                    Extra: Last beacon: 3596ms ago
                    IE: Unknown: 0006354136343944
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500001A127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 11 - Address: 00:25:2E:AE:4E:2B
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"97845C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000545fe2585c
                    Extra: Last beacon: 3380ms ago
                    IE: Unknown: 0006393738343543
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1603080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



Hmmm,,,seems root can use the wireless.....checking permissions.....

---

### Post by Gutsanglory on 2011-02-25
YEAHHHHH !!!

Well, it seems that in 10.10 by default the user is not allowed to "access wireless networks" under the system, administration, users and groups dilog box. I check marked this option, and low and behold, after a reboot, when I click the network manager, I see networks, I have connected to one, and am writing this through my wireless connection.


MAJOR thanks to Chilli555 and Walt for the help!!


:popcorn: :-P

Guts

---

### Post by walt.smith1960 on 2011-02-25
Excellent!!  I don't know why using a modem for networking is enabled by default but wireless is not.  There are some "interesting" user hardware defaults.

---

