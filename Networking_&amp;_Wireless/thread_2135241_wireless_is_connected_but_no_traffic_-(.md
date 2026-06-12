---
title: "wireless is connected but no traffic :-("
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by shahav on 2013-04-13
Hi guys, 
I'm kind of lost, your help is well appreciated.

I've recently changed my access point at home, and since then I can't hook to netowrk using the wifi at home. wireless is connected, ip seems to be valid, but no ping, zero traffic.
Note that i'm capable to use other wifi networks. also note that on my home network all other computes work just fine with the new ap. moreover this laptop is also conecting fine to the new ap  through micro$oft

10x
R.

Here is the raw data:
```

pc1941-r53653::~>lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor

pc1941-r53653::~>lspci 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller RAID mode (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0a:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
0a:00.1 Mass storage controller: O2 Micro, Inc. Device 8231 (rev 03)

pc1941-r53653::~>ifconfig 
eth0      Link encap:Ethernet  HWaddr 5c:26:0a:6e:5c:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:654605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:617542265 (617.5 MB)  TX bytes:81231161 (81.2 MB)
          Interrupt:20 Memory:e2e00000-e2e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61566111 (61.5 MB)  TX bytes:61566111 (61.5 MB)

wlan1     Link encap:Ethernet  HWaddr a0:88:b4:a0:54:78  
          inet addr:10.100.101.107  Bcast:10.100.101.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fea0:5478/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14103737 (14.1 MB)  TX bytes:3684692 (3.6 MB)

pc1941-r53653::~>iwconfig 
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"Shahav-012"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:90:8F:39:D5:58   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:0

eth0      no wireless extensions.

pc1941-r53653::~>
pc1941-r53653::~>lsmod
Module                  Size  Used by
cdc_acm                26858  0 
usb_storage            49198  0 
nls_utf8               12557  1 
isofs                  40257  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
kvm_intel             137721  0 
kvm                   415549  1 kvm_intel
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
parport_pc             32866  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
wmi                    19256  1 dell_wmi
i915                  473035  3 
serio_raw              13211  0 
mac_hid                13253  0 
iwlwifi               332525  0 
mac80211              506816  1 iwlwifi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
soundcore              15091  1 snd
cfg80211              205544  2 iwlwifi,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 


pc1941-r53653::~> sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 5c:26:0a:6e:5c:6c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:e2e00000-e2e1ffff memory:e2e80000-e2e80fff ioport:4080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 34
       serial: a0:88:b4:a0:54:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-30-generic firmware=18.168.6.1 ip=10.100.101.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e2d00000-e2d01fff


pc1941-r53653::~>iwlist scan
lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:90:8F:39:D5:58
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Shahav-012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000012576914b
                    Extra: Last beacon: 11260ms ago
                    IE: Unknown: 000A5368616861762D303132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500031D7A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C33EE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404050700000000000000000000000000000000000000
          Cell 02 - Address: C0:AC:54:F7:CD:7E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"HOTBOX-9C42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 14660ms ago
                    IE: Unknown: 000B484F54424F582D39433432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD750050F204104A0001101044000102103B00010310470010FBB1440E7884F138EA213D6C4F3DF8FD1021000846405354333138341023000846405354333138341024000631323334353610420007303030303030311054000800060050F204000110110006484F54424F58100800020088103C000101
                    IE: Unknown: DD090010180203F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:12:2A:10:C5:3B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b4076b15c
                    Extra: Last beacon: 14656ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706494C20010B14
                    IE: Unknown: DD380050F204104A0001101044000102104100010110120002000010530002008410470010BC329E001DD811B2860100122A10C53B103C000100
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000F7A12
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: 00:12:2A:39:B2:2C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Carmit"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000668695151
                    Extra: Last beacon: 14644ms ago
                    IE: Unknown: 00064361726D6974
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860100122A39B22C103C000100
                    IE: Unknown: 050402030004
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001137A12
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: 4C:60:DE:4A:03:9B
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"landau"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000953fd520f7
                    Extra: Last beacon: 14616ms ago
                    IE: Unknown: 00066C616E646175
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD920050F204104A00011010440001011041000100103B0001031047001000FBD21E7B9A8EF942EBB6054E2FB2CF1021000D4E4554474541522C20496E632E1023000E44474E32323030763242455A45511024000E44474E32323030763242455A455110420004323230301054000800060050F20400011011000E44474E32323030763242455A4551100800020084103C000101
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 98:0C:82:81:2D:4F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"shahav3g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000093a03250
                    Extra: Last beacon: 14284ms ago
                    IE: Unknown: 00087368616861763367
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1019FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD09001018020000000000
          Cell 07 - Address: F0:7D:68:FA:B9:EB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5ab20200c
                    Extra: Last beacon: 14460ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: F8:D1:11:BA:C4:48
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Smile-r "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d15dc720f
                    Extra: Last beacon: 14512ms ago
                    IE: Unknown: 0008536D696C652D7220
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 331A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071500000000000000000000000000000000000000
                    IE: Unknown: 341606071500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B0001031047001000000000000010000000F8D111BAC4101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 09 - Address: 00:78:9E:FB:5D:40
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HOTBOX-gio298"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0e1486558
                    Extra: Last beacon: 14108ms ago
                    IE: Unknown: 000D484F54424F582D67696F323938
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001F00000000000000000000000000000000000000
                    IE: Unknown: DD750050F204104A0001101044000102103B000103104700102AA377EFBBEC7C971383B0AF10ACDEFC1021000846405354333138341023000846405354333138341024000631323334353610420007303030303030311054000800060050F204000110110006484F54424F58100800020088103C000101
                    IE: Unknown: DD090010180204F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

pc1941-r53653::~> lsb_release -d
Description:	Ubuntu 12.04.1 LTS

pc1941-r53653::~> lsb_release -d
Description:	Ubuntu 12.04.1 LTS
pc1941-r53653::~>uname -mr
3.2.0-30-generic x86_64
pc1941-r53653::~>sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                              OK
```

---

### Post by chili555 on 2013-04-13
Please check here. You have a very similar condition and need the same fix: [http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable)

---

### Post by shahav on 2013-04-13
> **chili555 said:**
> Please check here.You have a very similar condition and need the same fix: [http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable)

10x for the fast reply.
indeed sutting off the 11n on the iwlwifi module solved the issue. 

How did u know? what was the clue?

10x again.
R.

---

### Post by chili555 on 2013-04-13
The clue was this:>  wireless is connected, ip seems to be valid, but no ping, zero traffic....and this:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       logical name: wlan1
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=iwlwifi[/COLOR] driverversion=3.2.0-30-genericI've seen, over the years, on this and other forums, variations of this same thing dozens of times. The fix is 99% of the time 11n_disable=1. It's a well-known iwlwifi bug. 

I'm glad it's working.

---

### Post by George_Sakhnovsky on 2013-08-07
.

---

