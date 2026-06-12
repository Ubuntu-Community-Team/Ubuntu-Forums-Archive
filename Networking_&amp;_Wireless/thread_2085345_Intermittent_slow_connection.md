---
title: "Intermittent slow connection"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by alienhawk on 2012-11-17
Hi, I am new so forgive me if I don't do this correctly.  I was wondering if someone could help with my connection.  When I run windows, the connection is good.  Web pages pop right up, pandora plays music without stopping, etc.  When I first set up 12.04, my connection was just as good, however the last 5 weeks, my connection has gotten worse.  Speetest, will give me a .02 download speed, while windows gives me 9.  Both on same network.  I have tried several of the suggestions found in the forums but none seem to work for me.  Instead of just shooting in the dark, I thought I would try this.  
My router is Linksys E2500
Below is some data:
Forgive me for just listing it all, not sure what is pertinent.

[SIZE=1]bill@bill-GA-MA770T-UD3:~$ ping [www.google.com]("http://www.google.com") -c 20
PING [www.google.com]("http://www.google.com") (74.125.225.180) 56(84) bytes of data.
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=1 ttl=55 time=39.3 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=2 ttl=55 time=36.8 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=3 ttl=55 time=36.9 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=7 ttl=55 time=36.4 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=8 ttl=55 time=36.3 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=11 ttl=55 time=40.1 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=12 ttl=55 time=39.4 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=13 ttl=55 time=36.9 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=15 ttl=55 time=547 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=16 ttl=55 time=420 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=17 ttl=55 time=36.3 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=18 ttl=55 time=37.0 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=19 ttl=55 time=38.9 ms
64 bytes from den03s05-in-f20.1e100.net (74.125.225.180): icmp_req=20 ttl=55 time=36.3 ms

--- [www.google.com]("http://www.google.com") ping statistics ---
20 packets transmitted, 14 received, 30% packet loss, time 27352ms
rtt min/avg/max/mdev = 36.349/101.353/547.633/158.011 ms

bill@bill-GA-MA770T-UD3:~$ modinfo rt61pci
filename:       /lib/modules/3.2.0-33-generic-pae/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     4E4E25FECFF46026C4F8BCC
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,crc-itu-t,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-33-generic-pae SMP mod_unload modversions 686 
parm:           nohwcryptisable hardware encryption. (bool)

bill@bill-GA-MA770T-UD3:~$ sudo iwlist scan
sudo: unable to resolve host bill-GA-MA770T-UD3
[sudo] password for bill: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:AA:4B:C2:03:51
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption keyn
                    ESSID:"Dol Guldur"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dd3c22a7b
                    Extra: Last beacon: 696ms ago
                    IE: Unknown: 000A446F6C2047756C647572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010ED05F204F94E77D3B54B8552CC05730410210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: C0:3F:0E:18:B1:C6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption keyn
                    ESSID:"Briano-PC-Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004a0f48b0c9d
                    Extra: Last beacon: 1556ms ago
                    IE: Unknown: 0012427269616E6F2D50432D576972656C657373
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001030AE3B76E6EA3C7343D799247C30984C1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:00:00:00:00:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption keyn
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000022265b23b70
                    Extra: Last beacon: 1568ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 28:CFA:B2:9F:BF
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption keyn
                    ESSID:"Chuck & Missy's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005e21c290196
                    Extra: Last beacon: 1484ms ago
                    IE: Unknown: 0017436875636B2026204D697373792773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301740320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010628CFDAB29FBF
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 05 - Address: 84:1B:5E:00:07:A5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption keyn
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c64ab6b183
                    Extra: Last beacon: 1224ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010110470010A3E4F37599CC60442AA691BDFBA1F267103C000103
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 44:A7:CF:5F:017
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption keyn
                    ESSID:"Verizon MiFi2200 01D7 Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000031d35f17a
                    Extra: Last beacon: 1168ms ago
                    IE: Unknown: 001C566572697A6F6E204D69466932323030203031443720536563757265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 20:AA:4B:C2:03:53
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption keyff
                    ESSID:"Dol Guldur-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dd3c25843
                    Extra: Last beacon: 684ms ago
                    IE: Unknown: 0010446F6C2047756C6475722D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

bill@bill-GA-MA770T-UD3:~$ sudo lshw -C network
sudo: unable to resolve host bill-GA-MA770T-UD3
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:a7:ca:b3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 00
       serial: 00:19:db:05:63:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.2.0-33-generic-pae firmware=0.8 ip=192.168.1.137 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fddf0000-fddf7fff

bill@bill-GA-MA770T-UD3:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
vesafb                 13516  1 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt61pci                27462  0 
rt2x00pci              14202  1 rt61pci
rt2x00lib              48836  2 rt61pci,rt2x00pci
mac80211              436455  2 rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
wmi                    18744  0 
mac_hid                13077  0 
eeprom_93cx6           12653  1 rt61pci
fglrx                2909855  130 
psmouse                86486  0 
serio_raw              13027  0 
parport_pc             32114  1 
soundcore              14635  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
k10temp                12990  0 
i2c_piix4              13093  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  2 rt61pci,firewire_core
floppy                 60310  0 
pata_atiixp            12999  0 
r8169                  56321  0 


bill@bill-GA-MA770T-UD3:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


bill@bill-GA-MA770T-UD3:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper XT [AMD Radeon HD 6000 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
bill@bill-GA-MA770T-UD3:~$ [/SIZE]

[SIZE=1]bill@bill-GA-MA770T-UD3:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Dol Guldur"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 20:AA:4B:C2:03:51   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:171  Invalid misc:852   Missed beacon:0

eth0      no wireless extensions.
[/SIZE]
Thank you!!!

---

