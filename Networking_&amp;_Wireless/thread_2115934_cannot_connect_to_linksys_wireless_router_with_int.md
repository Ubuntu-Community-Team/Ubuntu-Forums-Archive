---
title: "cannot connect to linksys wireless router with intel radio"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by RifledParrot on 2013-02-14
I'm trying to connect Ubuntu 11 to a linksys wireless router. The system repeatedly prompts for the password,  trys to connect and then asks for the password again. It can see the router, and all my neighbor's as well but will not connect. An iphone and Windows laptop do connect. The pass word is "Gandolf the Grey" and terminal data follows. Any help is appreciated.

```

jtcox@jtcox-desktop:~$ sudo lshw -C network
[sudo] password for jtcox: 

DMI
SMP
PA-RISC
device-tree
SPD
memory
/proc/cpuinfo
CPUID
PCI (sysfs)
ISA PnP
PCMCIA
PCMCIA
kernel device tree (sysfs)
USB
IDE
SCSI
Network interfaces
Framebuffer devices
Display
CPUFreq
ABI
  *-network
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:2c:eb:18
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:21 memory:fae7c000-fae7cfff ioport:d080(size=8) memory:fae7e400-fae7e4ff memory:fae7e000-fae7e00f
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:a7:ec:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-34-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:41 memory:febfe000-febfffff

jtcox@jtcox-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

jtcox@jtcox-desktop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

jtcox@jtcox-desktop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:B8:C6:1A:71
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"4HCDN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b533ce4e6d
                    Extra: Last beacon: 2936ms ago
                    IE: Unknown: 0005344843444E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:12:17:B0:02:01
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"maynard"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cd9468188
                    Extra: Last beacon: 3176ms ago
                    IE: Unknown: 00076D61796E617264
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010100
          Cell 03 - Address: 00:14:BF:CD:F8:0C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011b2d048256
                    Extra: Last beacon: 3168ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F4000000
          Cell 04 - Address: 50:67:F0:EF:C0:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DAN-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003bfa3323b
                    Extra: Last beacon: 3104ms ago
                    IE: Unknown: 000E44414E2D50435F4E6574776F726B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: C0:C1:C0:44:86:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Tanner"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007889bd59186
                    Extra: Last beacon: 2972ms ago
                    IE: Unknown: 000654616E6E6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000

eth0      Interface doesn't support scanning.


jtcox@jtcox-desktop:~$ iwlist chan
lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
eth0      no frequency information.

jtcox@jtcox-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:c6:a7:ec:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jtcox@jtcox-desktop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:00:00:00:00:00
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000332a5bb28b
                    Extra: Last beacon: 3056ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

eth0      Interface doesn't support scanning.

jtcox@jtcox-desktop:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ether[01;31m[Knet[m[K controller [0200]: NVIDIA Corporation MCP79 Ether[01;31m[Knet[m[K [10de:0ab0] (rev b1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:a108]
    Kernel driver in use: forcedeth
[36m[K--[m[K
04:00.0 [01;31m[KNet[m[Kwork controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi

jtcox@jtcox-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:0829 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 

jtcox@jtcox-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    94575  1 
crc_itu_t              12707  1 udf
dm_crypt               23125  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_usb_audio         122982  1 
arc4                   12529  2 
nvidia              12319264  40 
snd_usbmidi_lib        25395  1 snd_usb_audio
uvcvideo               72627  0 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
dm_multipath           23230  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwlwifi               397012  0 
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
videodev               98259  1 uvcvideo
mac80211              506816  1 iwlwifi
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
psmouse                97443  0 
serio_raw              13211  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
cfg80211              205544  2 iwlwifi,mac80211
shpchp                 37277  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
binfmt_misc            17540  1 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
wmi                    19256  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
forcedeth              63460  0 

```

---

### Post by |{urse on 2013-02-14
Its spelled Gandalf. Is that maybe why?

---

### Post by RifledParrot on 2013-02-14
It is "Gandolf" in the passphrase and I just checked on the phone to be sure. I'd love to say I spelled it that way for security but It has been long enough I cannot recall.

---

