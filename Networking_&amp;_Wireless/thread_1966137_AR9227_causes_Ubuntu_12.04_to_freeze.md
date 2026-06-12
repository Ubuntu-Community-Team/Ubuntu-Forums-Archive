---
title: "AR9227 causes Ubuntu 12.04 to freeze"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Godspell on 2012-04-26
I am going to follow the guideline from "**HOWTO post a Wireless issue (ticket)**" in describing my problem.

**0) Problem briefly described**

An old problem. Same happened on Ubuntu 10.04, 11.10, openSUSE 12.1 and Fedora 16.
Installed OS from a pendrive. Installation went well, no problem at all.
The OS can be personalised, configured and used as long as is not connected to the Internet. Internet is connected via home wireless connection. Connecting to it is not a problem. The problem is once it is connected, the OS freezes and has to be hard-shutdown.

Tried **nohwcrypt=1** fix but did not work.
Even if the OS does not freeze immediately after connected, it freezes the moment the network is used e.g. checking for software updates. 

Have not tried the cable connection. It is kind of impossible to set up one.

All info below were taken from Ubuntu with wireless disconnected. This thread is prepared on Windows.

[B]1) Machine Brand and Model (PC/Laptop)
[/B]
```
This is a custom built desktop PC.
Motherboard -- Asrock N68-S3 UCC
CPU -- AMD Phenom 2 X4 AM3 3.3 GHz
GPU -- MSI ATI Radeon HD 5450 1GB
RAM -- 8GB DDR3 1333
HDD -- 750GB SATA2 7200RPM, 80GB IDE 7200RPM (<---Ubuntu partition with 8GB swap)
PCI Wireless card -- TP-LINK TL-WN851ND
```[B]

2) Wireless Brand, Model and Wireless Chipset:[/B]
```
xxxxx@asdf:~$ sudo lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:08.0 Network controller: Atheros Communications Inc. AR9227 Wireless Network Adapter (rev 01)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
``````
xxxxx@asdf:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:081b Logitech, Inc. Webcam C310
Bus 002 Device 002: ID 046d:c52e Logitech, Inc.
``````
xxxxx@asdf:~$ lspci -nn | grep 'Atheros'
01:08.0 Network controller [0280]: Atheros Communications Inc. AR9227 Wireless Network Adapter [168c:002d] (rev 01)
```[B]

3) Check interface:
[/B]```
xxxxx@asdf:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:d4:72:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20704 (20.7 KB)  TX bytes:20704 (20.7 KB)

wlan0     Link encap:Ethernet  HWaddr f4:ec:38:db:dd:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
xxxxx@asdf:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.
``````
xxxxx@asdf:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```[B]

4) check for modules:[/B]
```
xxxxx@asdf:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_via      51398  1 
arc4                   12529  2 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
psmouse                87603  0 
ppdev                  17113  0 
snd_hda_intel          33773  5 
snd_usb_audio         122982  1 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
ath9k                 132390  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              506816  1 ath9k
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
parport_pc             32866  1 
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  3 ath9k,mac80211,ath
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
mac_hid                13253  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
edac_core              53746  0 
k10temp                13166  0 
soundcore              15091  1 snd
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
radeon                804372  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
sata_nv                32286  0 
forcedeth              63460  0 
pata_amd               14118  2
``````
xxxxx@asdf:~$ lsmod | grep "ath"
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
```[B]

5) Kernel boot messages
[/B]```
alfred@asdf:~$ dmesg | grep "ath"
[   16.213970] ath9k 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[   16.517723] ath: EEPROM regdomain: 0x809c
[   16.517727] ath: EEPROM indicates we should expect a country code
[   16.517728] ath: doing EEPROM country->regdmn map search
[   16.517729] ath: country maps to regdmn code: 0x52
[   16.517731] ath: Country alpha2 being used: CN
[   16.517732] ath: Regpair used: 0x52
[   16.524064] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.524534] Registered led device: ath9k-phy0
[   16.585557] type=1400 audit(1335479733.136:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=943 comm="apparmor_parser"
[   40.175779] type=1400 audit(1335479756.724:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2010 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```When I did just **dmesg** as suggested, there were loads of lines. I couldn't even select them properly to copy. So instead, I decided to get msg only related to "ath".
If you do need all of them, let me know how to output them into a text file from terminal. It'd be easier for me that way.

**6) Network configuration**
```
xxxxx@asdf:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9227 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: f4:ec:38:db:dd:55
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbef0000-fbefffff
```[B]

7) Scan for networks:[/B]
```
xxxxx@asdf:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.
```[B]

Eight) Ubuntu Version:[/B]
```
xxxxx@asdf:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS
```**9) Kernel/architecture (including 32 vs. 64 bit):**
```
xxxxx@asdf:~$ uname -mr
3.2.0-23-generic x86_64
```[B]

10) Restarting the network:[/B]
```
xxxxx@asdf:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 
```Advice, suggestion and discussion are welcome. This is a fairly powerful machine (at least imho) and I am quite anxious to run Ubuntu on it. So, please help :)
Should you require any further info, do let me know.

Thank you very much. Best regards.

---

### Post by Godspell on 2012-04-28
I understand the forums are pretty busy with Pangolin release and receiving high number of bug reports, etc. That is why I waited for more than 24 hours to get a reply.

There hasn't been any reply so I'm wondering if there is still no solution for this.
The Kernel version jumped to 3.2 and I thought that was going to fix the problem but it didn't. Still maybe there is something I can do to resolve this without getting a new wireless card (as it works amazingly well on Windows).

The problem with AR9227 was since 10.04 so two years ago.
I vaguely understand that this has more to do with the manufacturer not providing support for Linux. The Kernel did and does have a module "ath9k" which supposedly works with all these chipsets but apparently is problematic. That is as far as I understand. My knowledge with dev matters are very limited.
I tried **nohwencrypt=1** but didn't work. The moment there's network traffic, the PC freezes.

Please, help me resolve this problem once and for all. Or at least, let me know more about it so I know what to keep an eye on in the future.

Thank you very much. Best regards.

---

### Post by praseodym on 2012-04-28
Please show the outputs of:

```
iwlist chan
sudo iwlist scan
```
Country code for China (CN)?! Try
```

sudo apt-get install iw
iw reg get
sudo iw reg set UK
iw reg get
sudo /etc/init.d/networking restart
```

---

### Post by Godspell on 2012-04-28
> **praseodym said:**
> Please show the outputs of:

```
iwlist chan
sudo iwlist scan
```Country code for China (CN)?! Try
```

sudo apt-get install iw
iw reg get
sudo iw reg set UK
iw reg get
sudo /etc/init.d/networking restart
```

I did as you said, mate, and followings are the results.

```

xxxxx@asdf:~$ iwlist chan
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
eth0      no frequency information.

``````

xxxxx@asdf:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 06:21:04:9B:95:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000116ccea8168
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:26:91:35:58:12
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKY22545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000092246525008
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 0008534B593232353435
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0505000100FC05
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180209F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:26:44:EF:AA:BD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"O2wi-fi_ALDI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004d628c321a7
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 000C4F3277692D66695F414C4449
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD09001018020300050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 04 - Address: E8:39:DF:FF:80:6F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-FF806D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f363ca21
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D464638303644
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9C0050F204104A0001101044000102103B000103104700106304125310192006122800E04C8670011021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100114144534C204D6F64656D2F526F75746572100800020082
                    IE: Unknown: DD1E00904C330E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 05 - Address: 74:44:01:6A:BB:85
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"IKEA.Southampton44152"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb0b7f9f6f
                    Extra: Last beacon: 396ms ago
                    IE: Unknown: 0015494B45412E536F757468616D70746F6E3434313532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407080400000000000000000000000000000000000000
          Cell 06 - Address: E0:CA:94:06:07:A0
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"O2wireless068000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005db871c4dc
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 00104F32776972656C657373303638303030
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0103FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503000B127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C330C0103FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A000700000000000000000000000000000000000000
          Cell 07 - Address: 00:01:E3:EF:4C:E4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"OrangeEF4CE2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002653b1ef
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000C4F72616E6765454634434532
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 90:01:3B:1A:A3:7D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SKYAA37C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000069885c0c
                    Extra: Last beacon: 788ms ago
                    IE: Unknown: 0008534B594141333743
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010BF34E8F4BCCD795C60175268405D9B841021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:21:04:9B:95:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-7RZK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000116cceb3fc2
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 000F4254486F6D65487562322D37525A4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: 0A:21:04:9B:95:DA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000116cceaed22
                    Extra: Last beacon: 776ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 11 - Address: E8:BE:81:67:27:C7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SKY10182"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000827dc26a009
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 0008534B593130313832
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000

eth0      Interface doesn't support scanning.
``````


xxxxx@asdf:~$ sudo apt-get install iw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
iw is already the newest version.
iw set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

xxxxx@asdf:~$ iw reg get
country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)

xxxxx@asdf:~$ sudo iw reg set UK

xxxxx@asdf:~$ iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

xxxxx@asdf:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 


```After changing the country code to UK, I connected to the wifi just to see if there would be any improvements, but no; the PC froze. I rebooted to try again, same result.
Btw, my home network's name is **O2wi-fi_ALDI**.

Let me know if you find anything interesting from those results.
Thank you very much.

---

### Post by praseodym on 2012-04-28
Change the encryption to WPA2-AES (CCMP) instead of mixed WPA/WPA2 and the channel to fixed 7 or 13, there is too much traffic on channel 1. Router firmware is up-to-date?

---

### Post by Godspell on 2012-04-28
> **praseodym said:**
> Change the encryption to WPA2-AES (CCMP) instead of mixed WPA/WPA2 and the channel to fixed 7 or 13, there is too much traffic on channel 1. Router firmware is up-to-date?

I don't know much about network security encryption and have always used WPA/WPA2.
As for the channels, I've never touched them. They've always worked great on Windows. I use Ubuntu on my laptop and it has never had a problem with my home connection either. (Btw, my laptop's wireless card is built-in and not ath9k.)
If I edit these details, wouldn't that affect the security and quality of the connection?

Anyway, the encryption types available on the router are WEP and WPA-PSK.
Atm WPA-PSK is chosen.
In WPA-PSK version, there are WPA, WPA2 and WPA+WPA2.
I've selected WPA2 but there is no WPA2-AES.
I've also changed the channels to manual and selected 13.

The router's drivers probably aren't updated cause I've never fiddled with them. It's a default Thomson router from O2. I don't know how to update it either. Tbh, I don't want to play around with it. If something breaks, I'll have to call them and pay for it. Not to mention the period without the Internet.

Other that that, as mentioned above, I've edited my home connection.

Anyway, so I tried again but still the same problem. Things are working just fine until I use the Internet...be that checking for software updates or firing up the Firefox, it just freezes outright. Thus, nothing changes there.

---

### Post by IwakiPingu on 2012-05-03
Do we have a solution for this issue in the meantime?

I also have the exact same WiFi card (TP-Link TL-WN851ND) and also experiencing the same issue. Connecting through LAN is working well, the crash only happens when I'm on wifi.

---

### Post by Godspell on 2012-05-03
> **IwakiPingu said:**
> Do we have a solution for this issue in the meantime?

I also have the exact same WiFi card (TP-Link TL-WN851ND) and also experiencing the same issue. Connecting through LAN is working well, the crash only happens when I'm on wifi.

There doesn't seem to be ANY solution whatsoever. Imo, there never was.
I have tried other distros such as Fedora, openSUSE and Debian; and they all had same problem with this wireless card. I remember posting this on Fedora forums last year (I think) but after a while, we just reached to a conclusion that this can't be solved.
Kind of a shame though, isn't it? I don't know about you but I was hoping to finally use Ubuntu on my desktop (cause 12.04 has got newer kernel and all) :|

---

### Post by IwakiPingu on 2012-05-03
ah shucks!

Actually I'm running ubuntu as the only OS, I kinda have no choice since my work really needs me to run linux (embedded dev). Besides one of these days gaming is not really an option either, so I don't really have any use of Windows anymore.

Now I gotta keep annoying the wifey with my 20m LAN cable and potentially tripping any unsuspecting visitor :lolflag:


Thanks for the quick reply! 


> **Godspell said:**
> There doesn't seem to be ANY solution whatsoever. Imo, there never was.
I have tried other distros such as Fedora, openSUSE and Debian; and they all had same problem with this wireless card. I remember posting this on Fedora forums last year (I think) but after a while, we just reached to a conclusion that this can't be solved.
Kind of a shame though, isn't it? I don't know about you but I was hoping to finally use Ubuntu on my desktop (cause 12.04 has got newer kernel and all) :|

---

### Post by Godspell on 2012-05-03
> **IwakiPingu said:**
> ah shucks!

_**Actually I'm running ubuntu as the only OS, I kinda have no choice since my work really needs me to run linux (embedded dev).**_ Besides one of these days gaming is not really an option either, so I don't really have any use of Windows anymore.

Now I gotta keep annoying the wifey with my 20m LAN cable and potentially tripping any unsuspecting visitor :lolflag:


Thanks for the quick reply!

No worries, wish I was more helpful.

Great to know Ubuntu still works with cable connection and wouln't crash until wireless is used. Had never tested it myself.

Jesus Christ! Holy Mother of God! Don't mind my geekgasm LOL
You're an embedded software developer who HAS to use Linux at work!? In other words, you're an IT professional who uses Linux for like what...6, 7 hours a day in and out every weekday.

WOW and DAMN, what I wouldn't give to get a job like that heh. It's like a holy grail of IT jobs.
I'm a University student and half of the guys in my class don't have any clue how to fix a PC or write a program.....or are even interested in to find out 'how things work'. The other half are too busy reading HCI theories and SDLC methodologies lol. On top of that, all of them don't seem to know the existence of Linux :|
So you can probably imagine where my excitement comes from lol Amongst all of those bloody academics, I'm like an outcast.

Anyway, sorry for an unrelated-rant-outbreak.

Btw, if you have a 20M cable, you can probably wire it overhead. You can use the wall sticker clippers to manage it. That way it's a little more permanent. Besides, you don't wanna get your missus tripped over and booted to the couch, do you lol

Best regards.

---

### Post by IwakiPingu on 2012-05-04
Godspell, read your PM :) 

For anyone running into the same issue, a thread here might help:
[https://bbs.archlinux.org/viewtopic.php?id=95395&p=2](https://bbs.archlinux.org/viewtopic.php?id=95395&p=2)

Apparently the ath9k kernel module has problem with 802.11n network, so just run the network on G only, and everything should be stable. I just briefly changed my access point settings (about 15minutes ago), so far no kernel panic.
 
Not the ideal solution, but ah well.

> **Godspell said:**
> No worries, wish I was more helpful.

Great to know Ubuntu still works with cable connection and wouln't crash until wireless is used. Had never tested it myself.

Jesus Christ! Holy Mother of God! Don't mind my geekgasm LOL
You're an embedded software developer who HAS to use Linux at work!? In other words, you're an IT professional who uses Linux for like what...6, 7 hours a day in and out every weekday.

WOW and DAMN, what I wouldn't give to get a job like that heh. It's like a holy grail of IT jobs.
I'm a University student and half of the guys in my class don't have any clue how to fix a PC or write a program.....or are even interested in to find out 'how things work'. The other half are too busy reading HCI theories and SDLC methodologies lol. On top of that, all of them don't seem to know the existence of Linux :|
So you can probably imagine where my excitement comes from lol Amongst all of those bloody academics, I'm like an outcast.

Anyway, sorry for an unrelated-rant-outbreak.

Btw, if you have a 20M cable, you can probably wire it overhead. You can use the wall sticker clippers to manage it. That way it's a little more permanent. Besides, you don't wanna get your missus tripped over and booted to the couch, do you lol

Best regards.

---

### Post by Godspell on 2012-05-08
> **IwakiPingu said:**
> Godspell, read your PM :) 

For anyone running into the same issue, a thread here might help:
[https://bbs.archlinux.org/viewtopic.php?id=95395&p=2](https://bbs.archlinux.org/viewtopic.php?id=95395&p=2)

Apparently the ath9k kernel module has problem with 802.11n network, so just run the network on G only, and everything should be stable. I just briefly changed my access point settings (about 15minutes ago), so far no kernel panic.
 
Not the ideal solution, but ah well.

My router is default O2 Thompson so doesn't have an editable option. But it works for you so it might be the same for others.
If anyone else has tried this out, please let us know.
Another thing that I've thought of is.....isn't there this thing called Ndiswrapper?? As far as I remember it's using Windows-compatible drivers on Linux. This was mainly for those devices that don't have opensource support. I really don't know much about it but I wonder if anybody has tried it before? Theoratically, the wireless card works flawlessly on Windows so using drivers from there on Ubuntu should do so, too.

Just my 5p worth :)

---

### Post by Dingers on 2012-05-27
I have the same problem :confused:

I'm running Ubuntu 10.04 x86 with an i5-750 and a p55 motherboard. I also have a TP-LINK TL-WN851ND. The freezing only started when I put this card in my rig about a week ago after having to move my router (no wired connection anymore :(). 

I saw the solution above about putting the router back to b/g. This isn't a very good solution for me as there are a few other devices on my network a fair distance from the router. They are really taking advantage of n's MIMO technology.

Has anyone found a fix? Perhaps there are some bleeding edge drivers around that may resolve the issue....

Thanks
Dingers

---

### Post by Godspell on 2012-05-27
> **Dingers said:**
> I have the same problem :confused:

I'm running Ubuntu 10.04 x86 with an i5-750 and a p55 motherboard. I also have a TP-LINK TL-WN851ND. The freezing only started when I put this card in my rig about a week ago after having to move my router (no wired connection anymore :(). 

I saw the solution above about putting the router back to b/g. This isn't a very good solution for me as there are a few other devices on my network a fair distance from the router. They are really taking advantage of n's MIMO technology.

Has anyone found a fix? Perhaps there are some bleeding edge drivers around that may resolve the issue....

Thanks
Dingers

So far, there is no fix for this (except to just use the G wireless like suggested above). I had to get a long cable for my PC to use LAN and disable the wireless. Either that or you're better off getting a new card. Personally, I'm not fond of that cause I use Windows 7 and the card works really good there.

So yeah, I'm afraid there's no fix at all.

Many thanks and regards.

---

### Post by Bivvy on 2012-06-02
Just installed this card (TL-WN851ND Wireless N PCI Adapter) in a  PC which my son has built and were getting the same problem... Arggh.
Worked fine when connected by cable but that means our router is not in the best place for all the other devices in the house.

The router is a Netgear DG834G running in mixed b/g mode (supporting an old Roku Soundbridge that only has 802.11b) - It does not support "n" so that's not the solution.

_Symptoms_
Everything seems to be working fine - for anything between 30 minutes and 2 hours
Sound seems to go into a loop for a few seconds
Screen goes black
Only way out is to hit the reset button.  

[U]Software
[/U]Ubuntu 12.04 - All updates installed

[U]Hardware
[/U]AMD Athlon II X3 455 
Biostar TA890GXE Motherboard  - built in graphics and audio.
8GB RAM

Any suggestions?

Thanks

---

### Post by praseodym on 2012-06-02
Try these boot parameters:

[http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572](http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572)

---

### Post by Godspell on 2012-06-03
> **praseodym said:**
> Try these boot parameters:

[http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572](http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572)

That page is German which means un-readable. Could you please make sure, for next time, that everything you post here is in English? So all of us can read it. Thank you.

For now, I've used Google Translate for it. Obviously, it's not all accurately translated but a little bit better than before. Here's the link:

[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fwlan-problem-mit-ar9287-pc-friert-ein%2F%23post-3584572&act=url]("http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Ftopic%2Fwlan-problem-mit-ar9287-pc-friert-ein%2F%23post-3584572&act=url")

Many thanks and regards.

---

### Post by praseodym on 2012-06-03
Found a similar one here ;)

[http://ubuntuforums.org/showthread.php?t=1846516&page=5&highlight=sudo+update+grub](http://ubuntuforums.org/showthread.php?t=1846516&page=5&highlight=sudo+update+grub)

Sorry, for not translating

---

### Post by mmascosta on 2012-10-11
Hi everyone!

First post here :)

I recently purchased an HTPC and added it a TL-WN851ND Wireless N PCI Adapter... I installed XBMCbuntu and, of course... as soon as I try to connect to the wireless network, the system freezes.

Any solution since the last post?

I'm also a newcomer to linux, so please be kind.. ;)

---

### Post by tb070 on 2012-10-29
Have AR928X, but froze after a day after latest update/grade Ubuntu 12.04.

sudo /etc/init.d/network-manager restart

Used this to start network manager and got connection again.

source:
[http://askubuntu.com/questions/148174/no-wifi-after-upgrading-12-04-kernel-to-3-2-0-24-generic-pae](http://askubuntu.com/questions/148174/no-wifi-after-upgrading-12-04-kernel-to-3-2-0-24-generic-pae)

---

