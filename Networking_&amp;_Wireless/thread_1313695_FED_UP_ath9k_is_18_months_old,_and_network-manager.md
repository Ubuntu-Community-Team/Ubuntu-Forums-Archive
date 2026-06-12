---
title: "FED UP: ath9k is 18 months old, and network-manager still drops connections on xfers"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by nightalon on 2009-11-03
I'm really annoyed.  I have an AR5008 PCI bgn card on a desktop and an AR5008X MiniPCI-E card on a laptop.

On all subsequent laptop purchases I have purchased Broadcom cards for this very reason: if I try to download a file larger than 10 MB, the connection drops or stalls.  This has been an issue EVER SINCE ATH9K WAS RELEASED.  

Apparently the DMA issues were fixed way back for kernel 2.6.29.  I hear this is a network-manager issue, but then why hasn't network-manager been patched properly?  What is the easiest way to use an alternate network manager?  THE STATUS QUO IS AWFUL, HAS BEEN THE CASE FOR 18 MONTHS, AND IS SYSTEM CHIPSET INDEPENDENT.

My AP is also Atheros-based and is a D-Link DIR-655 with the latest firmware.  I would go back to madwifi if it weren't also a mess.


**Laptop Info:**
Toshiba Tecra M7 running Ubuntu 9.10 64-bit

**LSPCI Output:**
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
**02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)**
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

IWCONFIG Output:
```
wlan0     IEEE 802.11abgn  ESSID:"TC-K54"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:58:FE:12:F3   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

LSMOD Output:
```
lsmod | grep "ath9k"
ath9k                 278176  0 
mac80211              210104  1 ath9k
ath                    10304  1 ath9k
led_class               5256  2 ath9k,sdhci
cfg80211              109144  3 ath9k,mac80211,ath

```

DMESG Output:
```
dmesg | grep "ath9k"
[   12.832499] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.832550] ath9k 0000:02:00.0: setting latency timer to 64
[   13.297152] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.299208] Registered led device: ath9k-phy0::radio
[   13.299266] Registered led device: ath9k-phy0::assoc
[   13.299411] Registered led device: ath9k-phy0::tx
[   13.299467] Registered led device: ath9k-phy0::rx
[  204.264521] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1311.541936] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1311.761981] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1311.982182] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1312.201920] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1312.421920] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1312.641840] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1312.862034] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1313.081899] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1313.302035] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1313.522099] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1313.741915] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1313.963829] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1314.182057] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1314.401952] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1314.621936] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1314.842125] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1315.074929] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1315.294521] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1315.514553] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1315.734536] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1315.952062] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1316.174407] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1316.392019] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1316.614584] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1316.834538] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
[ 1317.054527] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020

```

LSHW Output:
```
sudo lshw -C network
[sudo] password for brwillia: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 00
       serial: 00:15:b7:32:b2:54
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:ffae0000-ffafffff ioport:bfe0(size=32)
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:c6:4e:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.188 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:ff9f0000-ff9fffff

```

IWLIST Output:
```
wlan0     Scan completed :
          Cell 01 - Address: 06:1E:58:FE:12:F3
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"TC-K54 Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a1679a180
                    Extra: Last beacon: 5630ms ago
                    IE: Unknown: 000C54432D4B3534204775657374
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340907030000000F000000000000000000000000000000
          Cell 02 - Address: 00:1E:58:FE:12:F3
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"TC-K54"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a167b3180
                    Extra: Last beacon: 5550ms ago
                    IE: Unknown: 000654432D4B3534
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340907030000000F000000000000000000000000000000
          Cell 03 - Address: 00:0B:86:8D:3B:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000737152181
                    Extra: Last beacon: 6050ms ago
                    IE: Unknown: 000D79616C6520776972656C657373
                    IE: Unknown: 0108048B960C12182430
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32024860
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:0B:86:8D:3B:63
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"YaleGuest"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007371523c9
                    Extra: Last beacon: 6050ms ago
                    IE: Unknown: 000959616C654775657374
                    IE: Unknown: 0108048B960C12182430
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32024860
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:0B:86:8D:3B:64
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"YaleSecure"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000737152601
                    Extra: Last beacon: 6050ms ago
                    IE: Unknown: 000A59616C65536563757265
                    IE: Unknown: 0108048B960C12182430
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32024860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: 00:1A:1E:AD:DB:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000203310fce6
                    Extra: Last beacon: 6020ms ago
                    IE: Unknown: 000D79616C6520776972656C657373
                    IE: Unknown: 0108048B960C12182430
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32024860
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 96:57:52:43:6E:E5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"SETUP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00002ea1e05451e3
                    Extra: Last beacon: 5230ms ago
                    IE: Unknown: 00055345545550
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020010000000
          Cell 08 - Address: 00:19:5B:60:30:79
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"L32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025ad46a180
                    Extra: Last beacon: 5430ms ago
                    IE: Unknown: 00034C3332
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
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
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A00070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160A00030000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 09 - Address: 00:0B:86:8D:32:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"yale wireless"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c30fe181
                    Extra: Last beacon: 5420ms ago
                    IE: Unknown: 000D79616C6520776972656C657373
                    IE: Unknown: 0108048B960C12182430
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32024860
                    IE: Unknown: DD0A00037F04010000000000

```

Version Info:
```
brwillia@brwillia5:~$ lsb_release -d
Description:	Ubuntu 9.10
brwillia@brwillia5:~$ uname -mr
2.6.31-14-generic x86_64

```

*Please help!  I'm sure many people have this problem since I have it on two computers, a laptop and a desktop.*

---

### Post by frdrx on 2009-11-06
I can't promise you an improvement, but try to install the backported kernel modules, i.e., the linux-backports-modules-karmic-generic package if you use the generic kernel.

---

### Post by falconindy on 2009-11-06
Network manager is awful, and there's a plethora of threads eluding to this. Use Wicd instead, and look into the MadWifi drivers. Both should be in the repositories.

---

### Post by pastalavista on 2009-11-06
Is there another choice in System-> Administration-> Hardware Drivers? I believe, with your card, you should be using ath5k instead of ath9k.

---

### Post by nightalon on 2009-11-06
@pastalavista, no there is no other driver option.  ath9k was designed for AR5008 and higher, including, of course, the AR90xx and AR92xx series.  Do your research!  Thanks anyway.

@falconindy, thanks, I will look into using WICD.

@frdrx, thanks, I will try to use backports, but that also doesn't seem ideal.


I just don't understand why Windows XP/Vista/7 and MacOS X 10.4/.5/.6 was able to overcome the DMA issue, whereas the ath9k/network-manager combo never was able to.

Thanks for all your suggestions!  Keep them coming!

---

### Post by illuminatifire on 2010-03-05
I was having similar problems but primarily connecting to 802.11n networks, b nets worked fine.  I installed iw instead of using iwconfig and that didn't help as it is not a complete network manager.  It does allow me to set the network channels for the card but it lacks a lot of options, I still need to use iwconfig. The other thing I have noticed is that once I use it, it seems to cause drops in b networks.. I'll have to keep testing it to see if its just a coincidence.  I really have noticed little trouble other than getting it to work on b networks, the other problem is the lack of ability to choose the modulation with either iwconfig or iw, I think this is a driver issue.
Does anyone notice any problems with the Spash OS that comes pre-installed with HP? it is a linux OS and it doesn't seem to have as many networking issues with the card but I'm not sure how the networking card is configured or what programs it uses.

I am running kubuntu 9.10 kernel 2.6.31-19 and latest stable ath9k drivers, I have a HP dm3 with an AMD cpu.
sudo iw dev <wlan0> scan
sudo iw dev <wlan0> set type managed
sudo iw dev <wlan0> set channel <1>

---

