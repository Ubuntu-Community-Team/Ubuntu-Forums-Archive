---
title: "DWA 547 connectivity stability"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Jonhg on 2011-04-04
Hi,

I have an issue with my Dlink DWA 547 802.11n PCI adapter, I'm under LUCID fully updated.

I have no trouble connecting to any wireless but after a few minutes I'm loosing the connectivity strenght (getting ping reply from my router that vary from 2ms to 200ms). But as soon as I'm rescanning the network using the command (sudo iwlist wlan0 scan) everything is fine (constant 1-2ms ping). I'm using wicd as network manager. I have tried to schedule a job in crontab to launch every 10min a network scan command, but didn't succeed to have it working, morehover I don't think that's the good way.

Please advice, THX

---

### Post by Jonhg on 2011-04-05
Might help some others having the same issue:

Looks like it is more stable by installing the linux-backports-modules-compat-wireless-generic drivers.

;)

---

### Post by Jonhg on 2011-04-05
Sorry I just read the post "How to post a wireless issue", might be easier to help with this:

```

$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
05:06.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

$ lsusb
Bus 002 Device 002: ID 041e:30d0 Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 04f2:b021 Chicony Electronics Co., Ltd ViewSonic 1.3M, USB2.0 Webcam
Bus 001 Device 006: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 001 Device 005: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

$ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:21:91:0c:df:1c  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:91ff:fe0c:df1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4951052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6757412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3909188416 (3.9 GB)  TX bytes:4436699379 (4.4 GB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DIR615"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:E7:FD:A1:2E   
          Bit Rate=117 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ lsmod | grep "ath9k"
ath9k                  77491  0 
ath9k_common            3071  1 ath9k
mac80211              261570  2 ath9k,ath9k_common
ath9k_hw              239127  2 ath9k,ath9k_common
ath                    10345  2 ath9k,ath9k_hw
cfg80211              169518  4 ath9k,ath9k_common,mac80211,ath
led_class               3764  1 ath9k

```

```

dmesg | grep "ath9k"
[   32.065384] ath9k 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   32.609086] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   32.609796] Registered led device: ath9k-phy0::radio
[   32.609813] Registered led device: ath9k-phy0::assoc
[   32.609833] Registered led device: ath9k-phy0::tx
[   32.609851] Registered led device: ath9k-phy0::rx
[38527.182208] ath9k: Two wiphys trying to scan at the same time
[59074.687796]  [<ffffffffa0bf3f88>] ath_rx_tasklet+0x2a8/0x660 [ath9k]
[59074.687808]  [<ffffffffa0bf2c99>] ath9k_tasklet+0xf9/0x130 [ath9k]
[59074.698930]  [<ffffffffa0bf3f88>] ath_rx_tasklet+0x2a8/0x660 [ath9k]
[59074.698936]  [<ffffffffa0bf2c99>] ath9k_tasklet+0xf9/0x130 [ath9k]
[59074.709968]  [<ffffffffa0bf3f88>] ath_rx_tasklet+0x2a8/0x660 [ath9k]
[59074.709974]  [<ffffffffa0bf2c99>] ath9k_tasklet+0xf9/0x130 [ath9k]
[59074.721002]  [<ffffffffa0bf3f88>] ath_rx_tasklet+0x2a8/0x660 [ath9k]
[59074.721007]  [<ffffffffa0bf2c99>] ath9k_tasklet+0xf9/0x130 [ath9k]
[59074.732038]  [<ffffffffa0bf3f88>] ath_rx_tasklet+0x2a8/0x660 [ath9k]
[59074.732044]  [<ffffffffa0bf2c99>] ath9k_tasklet+0xf9/0x130 [ath9k]

```

```

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 01
       serial: 00:21:91:0c:df:1c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-30-generic firmware=N/A ip=192.168.1.3 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d8000000-d800ffff

```

```

sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:AD:A5:9B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"donna"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000615c193d183
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 0005646F6E6E61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 02 - Address: 00:18:E7:FD:A1:2E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"DIR615"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1dcc5b1b
                    Extra: Last beacon: 50ms ago
                    IE: Unknown: 0006444952363135
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

```

```

lsb_release -d
Description:	Ubuntu 10.04.2 LTS
uname -mr
2.6.32-30-generic x86_64

```

---

