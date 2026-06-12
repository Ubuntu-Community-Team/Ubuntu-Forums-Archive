---
title: "DLink wireless adapter is not working"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Diego Banda on 2009-12-15
I have a DWA-510 adapter on my computer, but it can't find connections available.
It was running well using Kubuntu 8.04, the issue is happening after Kubuntu 9.10 is installed.

Below are results of some command for help.

Can anybody help me with this?

Let me know if you need additional information.

Thanks in advance,
Diego Banda

```

# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

```

# uname -a
Linux judice 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

```

```

 # lspci -k
...
00:08.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci
...

```

```

 # lshw -C network
  *-network:0
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wmaster0
       version: 00
       serial: 00:1b:11:21:a3:a5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:e3000000-e3007fff
...

```

```

 # hwinfo --netcard              
12: PCI 08.0: 0282 WLAN controller                              
  [Created at pci.318]                                          
  UDI: /org/freedesktop/Hal/devices/pci_1814_302                
  Unique ID: y9sn.hGRXguAPhPB                                   
  SysFS ID: /devices/pci0000:00/0000:00:08.0                    
  SysFS BusID: 0000:00:08.0                                     
  Hardware Class: network                                       
  Model: "RaLink RT2561/RT61 rev B 802.11g"                     
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x0302 "RT2561/RT61 rev B 802.11g"
  SubVendor: pci 0x1186 "D-Link System Inc"
  SubDevice: pci 0x3a71
  Driver: "rt61pci"
  Driver Modules: "rt61pci"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xe3000000-0xe3007fff (rw,non-prefetchable)
  IRQ: 16 (no events)
  HW Address: 00:1b:11:21:a3:a5
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00000302sv00001186sd00003A71bc02sc80i00"
  Driver Info #0:
    Driver Status: rt61pci is active
    Driver Activation Cmd: "modprobe rt61pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
...

```

```

 # dmesg
...
[   17.552616] rt61pci 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.567573] parport_pc 00:09: reported by Plug and Play ACPI
[   17.567656] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   17.570380] cfg80211: World regulatory domain updated:
[   17.570388]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.570393]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.570397]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.570401]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.570405]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.570409]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.713458] lp0: using parport0 (interrupt-driven).
[   17.733438] irda_init()
[   17.733469] NET: Registered protocol family 23
[   17.761512] ppdev: user-space parallel port driver
[   17.788047] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.874754] phy0: Selected rate control algorithm 'minstrel'
[   17.875822] Registered led device: rt61pci-phy0::radio
[   17.875852] Registered led device: rt61pci-phy0::assoc
[   17.876623] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.045376] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   18.045383] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   18.045391]   alloc irq_desc for 22 on node -1
[   18.045395]   alloc kstat_irqs on node -1
[   18.045407] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   18.045581] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   18.066104] psmouse serio1: ID: 10 00 64
[   18.305142] EXT4-fs (sda3): barriers enabled
[   18.329438] kjournald2 starting: pid 667, dev sda3:8, commit interval 5 seconds
[   18.329700] EXT4-fs (sda3): internal journal on sda3:8
[   18.329706] EXT4-fs (sda3): delayed allocation enabled
[   18.329710] EXT4-fs: file extents enabled
[   18.337973] EXT4-fs: mballoc enabled
[   18.338082] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   18.602334] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   18.776179] type=1505 audit(1260886401.401:9): operation="profile_replace" pid=755 name=/sbin/dhclient3
[   18.776597] type=1505 audit(1260886401.401:10): operation="profile_replace" pid=755 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.776839] type=1505 audit(1260886401.401:11): operation="profile_replace" pid=755 name=/usr/lib/connman/scripts/dhclient-script
[   18.783059] type=1505 audit(1260886401.405:12): operation="profile_replace" pid=761 name=/usr/lib/cups/backend/cups-pdf
[   18.783596] type=1505 audit(1260886401.405:13): operation="profile_replace" pid=761 name=/usr/sbin/cupsd
[   18.787308] type=1505 audit(1260886401.409:14): operation="profile_replace" pid=762 name=/usr/sbin/mysqld-akonadi
[   18.790543] type=1505 audit(1260886401.413:15): operation="profile_replace" pid=763 name=/usr/sbin/tcpdump
[   19.121282] rt61pci 0000:00:08.0: firmware: requesting rt2561.bin
[   19.184729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.188560] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   22.087833] [drm] Initialized drm 1.1.0 20060810
[   22.091133] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.091378] [drm] Initialized savage 2.4.1 20050313 for 0000:01:00.0 on minor 0
[   29.696043] eth0: no IPv6 routers present

```

```

 # ifconfig wlan0
wlan0     Link encap:Ethernet  Endereço de HW 00:1b:11:21:a3:a5
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

```

 # iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=11 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

 # iwlist wlan0 scan
wlan0     No scan results

Running the same command in another computer, we can see the connection that I need to use:
...
          Cell 07 - Address: 00:1C:F0:F1:2C:06                                           
                    Channel:11                                                           
                    Frequency:2.462 GHz (Channel 11)                                     
                    Quality=46/70  Signal level=-64 dBm                                  
                    Encryption key:on                                                    
                    ESSID:"connectionNet"                                                
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s                          
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                  
                              36 Mb/s; 48 Mb/s; 54 Mb/s                                  
                    Mode:Master                                                          
                    Extra:tsf=000001b6e4ef8ac6                                           
                    Extra: Last beacon: 2950ms ago                                       
                    IE: Unknown: 000D636F6E6E656374696F6E4E6574                          
                    IE: Unknown: 010482848B96                                            
                    IE: Unknown: 03010B                                                  
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
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B00070000000F000000000000000000000000000000        
                    IE: Unknown: 2D1A6C101FFFFF000000000000000000000000000004000000000000        
                    IE: Unknown: 3D160B00000000000F000000000000000000000000000000                
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700106721358100093A34B9CD74F6672D26B01021000E442D4C696E6B2053797374656D73102300074449522D363335102400024231104200046E6F6E651054000800060050F204000110110019576972656C6573732044726166742031316E20526F75746572100800020004                                                                                                               

```

---

### Post by Diego Banda on 2009-12-17
I can't find any wireless connection available.
Can anybody help me, please?

Thanks

---

