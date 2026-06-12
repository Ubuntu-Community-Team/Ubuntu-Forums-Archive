---
title: "wireless disconnect when running on battery (Toshiba Satelite A215-S5818)"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by sk8 on 2012-06-13
I'm at wits end trying to figure out why I can NOT maintain a wifi connection while running on battery source. When connected to a power source I can usually get a connection, but once unplugged I keep a connection shortly then the connection is disabled. I'm curently running 12.04 Precise  on a Toshiba Satelite A215-S5818. I've tried to provide the information below but I understand it may be incomplete and/or un-useful. Thanks in advance for the help.


i'm also seeking help in #ubuntu on freenode

---

### Post by sk8 on 2012-06-13
I'm at wits end trying to figure out why I can NOT maintain a wifi connection while running on battery source. When connected to a power source I can usually get a connection, but once unplugged I keep a connection shortly then the connection is disabled. I'm curently running 12.04 Precise  on a Toshiba Satelite A215-S5818. I've tried to provide the information below but I understand it may be incomplete and/or un-useful. Thanks in advance for the help.


dmesg | grep iwl
rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lspci: 

sk8@nix-box:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Device 7914
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by sk8 on 2012-06-13
iwconfig (powersource connected):

sk8@nix-box:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CPL-PUBLIC"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: D8:24:BD:4E:0F:11   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:131   Missed beacon:0

eth0      no wireless extensions.

lsmod:

lsmod
Module                  Size  Used by
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
radeon                733693  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
video                  19068  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   17808  0 
psmouse                72919  0 
serio_raw              13027  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
i2c_algo_bit           13199  1 radeon
sp5100_tco             13495  0 
soundcore              14635  1 snd
k8temp                 12905  0 
i2c_piix4              13093  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
mac_hid                13077  0 
shpchp                 32325  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  0 
r8169                  56321  0

---

### Post by sk8 on 2012-06-13
sudo lshw -C network :


 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:94:4f:f0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:87:45:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-25-generic-pae firmware=N/A ip=172.16.2.212 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8200000-f820ffff


iwlist scan : 


lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: D8:24:BD:4E:0F:11
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"CPL-PUBLIC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010ae67f2978
                    Extra: Last beacon: 9456ms ago
                    IE: Unknown: 000A43504C2D5055424C4943
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E08009A000F00FF0319004150310000000000000000000000000000000036
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 02 - Address: D8:24:BD:4E:0F:10
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"CPL-PRIVATE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010ae67f2977
                    Extra: Last beacon: 9504ms ago
                    IE: Unknown: 000B43504C2D50524956415445
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1608000700000000000000000000000000000000000000
                    IE: Unknown: 851E08009A000F00FF0319004150310000000000000000000000000001000036
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 03 - Address: D8:24:BD:4E:50:50
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"CPL-PRIVATE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b3dc45978
                    Extra: Last beacon: 10764ms ago
                    IE: Unknown: 000B43504C2D50524956415445
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1602080400000000000000000000000000000000000000
                    IE: Unknown: 851E06009A000F00FF0319004150320000000000000000000000000000000036
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 04 - Address: D8:24:BD:4E:50:51
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"CPL-PUBLIC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b3dc2c177
                    Extra: Last beacon: 10924ms ago
                    IE: Unknown: 000A43504C2D5055424C4943
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E06009A000F00FF0319004150320000000000000000000000000000000036
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400

eth0      Interface doesn't support scanning.


i'm also seeking help in #ubuntu on freenode

---

### Post by sk8 on 2012-06-13
The above information is gathered while connected to a powersource and being able to connect to a wifi signal. I will gather information while i do NOT have a connection below in a few moments.

---

### Post by sk8 on 2012-06-13
```
sk8@nix-box:~$ dmesg | grep iwl
sk8@nix-box:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
sk8@nix-box:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Device 7914
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
sk8@nix-box:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

sk8@nix-box:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
ath5k                 145127  0 
psmouse                72919  0 
ath                    19387  1 ath5k
snd_seq_midi           13132  0 
serio_raw              13027  0 
mac80211              436455  1 ath5k
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
k8temp                 12905  0 
r592                   17808  0 
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
memstick               15857  1 r592
nand_ecc               13070  1 nand
soundcore              14635  1 snd
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178679  3 ath5k,ath,mac80211
radeon                733693  3 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
video                  19068  0 
i2c_algo_bit           13199  1 radeon
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
shpchp                 32325  0 
mac_hid                13077  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  0 
r8169                  56321  0 
sk8@nix-box:~$ sudo lshw -C network
[sudo] password for sk8: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:94:4f:f0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:87:45:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-25-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8200000-f820ffff
sk8@nix-box:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

sk8@nix-box:~$ 

```

This is the above information while Wifi was disconnected

---

### Post by sk8 on 2012-06-20
bump

---

