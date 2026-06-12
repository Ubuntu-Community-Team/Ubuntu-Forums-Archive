---
title: "Why does my wireless only work after restarting from Windows? (10.04)"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by danilosoares on 2010-07-23
Greetings,

I have recently installed Ubuntu 10.04 in one of my notebook's HD partitions. It all runs smoothly, except for wireless. For some reason, Ubuntu only finds my wireless connections after I boot into Windows and then restart. If I boot straight into Ubuntu, I always get the 'device not ready' or 'disconnected' message under 'Wireless networks'.

Does anyone know what might be the cause of the problem and what can I do to solve it?

Below are some information about my computer, as requested in the 'How to post a wireless issue' thread.

--

These are the results AFTER restarting from Windows.

Machine brand: Mirax - XT8000 NTL 243200

```
lspci

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:47:8f:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3030743 (3.0 MB)  TX bytes:3030743 (3.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:1c:3a:d7  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe1c:3ad7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7760401 (7.7 MB)  TX bytes:581435 (581.4 KB)

```

```
iwconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:47:8f:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3030743 (3.0 MB)  TX bytes:3030743 (3.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:1c:3a:d7  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe1c:3ad7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7760401 (7.7 MB)  TX bytes:581435 (581.4 KB)

```

```
lsmod
Module                  Size  Used by
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
rfcomm                 33421  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                105566  0 
iwlcore               105922  1 iwlagn
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  282354  3 
uvcvideo               56990  0 
btusb                  10925  2 
mac80211              204922  2 iwlagn,iwlcore
sdhci_pci               5470  0 
drm_kms_helper         29297  1 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
sdhci                  15462  1 sdhci_pci
led_class               2864  2 iwlcore,sdhci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126485  3 iwlagn,iwlcore,mac80211
psmouse                63245  0 
intel_agp              24177  2 i915
serio_raw               3978  0 
drm                   162471  4 i915,drm_kms_helper
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
r8169                  33884  0 
mii                     4381  1 r8169
ahci                   32008  2 
```

```
[   13.483091] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.483097] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.483218] iwlagn 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.483258] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.483342] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.565797] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   13.565908]   alloc irq_desc for 30 on node -1
[   13.565913]   alloc kstat_irqs on node -1
[   13.565945] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   13.682777] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.831536] r8169: eth0: link down
[   13.831919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.843594] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[   13.855371] type=1505 audit(1279941001.942:5):  operation="profile_load" pid=804 name="/usr/share/gdm/guest-session/Xsession"
[   13.855645] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   13.866212] type=1505 audit(1279941001.954:6):  operation="profile_replace" pid=806 name="/sbin/dhclient3"
[   13.867622] type=1505 audit(1279941001.954:7):  operation="profile_replace" pid=806 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.870139] type=1505 audit(1279941001.958:8):  operation="profile_replace" pid=806 name="/usr/lib/connman/scripts/dhclient-script"
[   13.876456] type=1505 audit(1279941001.966:9):  operation="profile_load" pid=808 name="/usr/bin/evince"
[   13.890875] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   13.906289] type=1505 audit(1279941001.994:10):  operation="profile_load" pid=808 name="/usr/bin/evince-previewer"

```

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:21:85:47:8f:3b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdfc0000-fdfdffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:1c:3a:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:fdefe000-fdefffff

```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:9A:F1:B6:19
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"mktdata"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ecde6cc992
                    Extra: Last beacon: 13080ms ago
                    IE: Unknown: 00076D6B7464617461
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:21:29:85:6F:8F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Venticinque"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000283a61d73f
                    Extra: Last beacon: 9008ms ago
                    IE: Unknown: 000B56656E746963696E717565
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1C:10:89:68:E4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Bufano"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b75e9d186
                    Extra: Last beacon: 12428ms ago
                    IE: Unknown: 0006427566616E6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 04 - Address: 00:1C:DF:CE:6A:4A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Ever_0902"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006e1a22183
                    Extra: Last beacon: 12256ms ago
                    IE: Unknown: 0009457665725F30393032
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDFCE6A4A1021000642656C6B696E1023000F463544373233302D342D763830303010240007575053303030311042000E32303832313732333031323233391054000800060050F204000110110020463544373233302D340000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:19:E0:96:C5:46
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BILLY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a650a22ea
                    Extra: Last beacon: 13056ms ago
                    IE: Unknown: 000542494C4C59
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 07065A5720010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000019E096C5460219E096C54664002C010808
          Cell 06 - Address: 00:1A:3F:4A:F1:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DKMB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008427271ea
                    Extra: Last beacon: 12676ms ago
                    IE: Unknown: 0004444B4D42
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706425220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F0301000000001A3F4AF100021A3F4AF10064002C010808
          Cell 07 - Address: 00:1B:11:E5:51:37
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"matbru"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e54ed6c15
                    Extra: Last beacon: 13036ms ago
                    IE: Unknown: 00066D6174627275
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F010100060000
                    IE: Unknown: DD0C00037F020101000002A34000
          Cell 08 - Address: 00:1F:33:22:70:E4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Japy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004140fc9181
                    Extra: Last beacon: 13088ms ago
                    IE: Unknown: 00044A617079
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 09 - Address: 00:18:F8:E2:62:E6
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"LIMA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dd9fbdca3
                    Extra: Last beacon: 12672ms ago
                    IE: Unknown: 00044C494D41
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:15:E9:DE:6A:DB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"21"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f9c5a7165
                    Extra: Last beacon: 12656ms ago
                    IE: Unknown: 00023231
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 11 - Address: 00:19:E0:A4:39:EE
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"biotech"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019cf1f7181
                    Extra: Last beacon: 12404ms ago
                    IE: Unknown: 000762696F74656368
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010C
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706425220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000019E0A439EE0219E0A439EE64002C010808

pan0      Interface doesn't support scanning.

```

```
uname -mr
2.6.32-21-generic i686

```

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                 Ignoring unknown interface wlan0=wlan0.

```

---

### Post by danilosoares on 2010-07-24
And here is what I get when I boot straight into Ubuntu:


```
lspci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Memory Stick Card Reader Controller
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```




```
ifconfig


eth0      Link encap:Ethernet  HWaddr 00:21:85:47:8f:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7737 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:949731 (949.7 KB)  TX bytes:949731 (949.7 KB)
```




```
iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.
```





```
lsmod


Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                105566  0 
iwlcore               105922  1 iwlagn
i915                  282354  3 
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  2 iwlagn,iwlcore
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162471  4 i915,drm_kms_helper
psmouse                63245  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 iwlcore,sdhci
cfg80211              126485  3 iwlagn,iwlcore,mac80211
intel_agp              24177  2 i915
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
video                  17375  1 i915
output                  1871  1 video
usbhid                 36110  0 
hid                    67032  1 usbhid
ahci                   32008  3 
r8169                  33884  0 
mii                     4381  1 r8169
```





```
dmesg


[   13.723309] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.723313] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.723417] iwlagn 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.723450] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.723727] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.821401] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   13.821479]   alloc irq_desc for 30 on node -1
[   13.821482]   alloc kstat_irqs on node -1
[   13.821507] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   13.827930] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.031038] type=1505 audit(1279974764.074:5):  operation="profile_load" pid=759 name="/usr/share/gdm/guest-session/Xsession"
[   14.033006] type=1505 audit(1279974764.078:6):  operation="profile_replace" pid=761 name="/sbin/dhclient3"
[   14.033768] type=1505 audit(1279974764.078:7):  operation="profile_replace" pid=761 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.034177] type=1505 audit(1279974764.078:8):  operation="profile_replace" pid=761 name="/usr/lib/connman/scripts/dhclient-script"
[   14.037918] type=1505 audit(1279974764.082:9):  operation="profile_load" pid=762 name="/usr/bin/evince"
[   14.050496] type=1505 audit(1279974764.094:10):  operation="profile_load" pid=762 name="/usr/bin/evince-previewer"
[   14.057339] type=1505 audit(1279974764.102:11):  operation="profile_load" pid=762 name="/usr/bin/evince-thumbnailer"
[   14.129316] r8169: eth0: link down
[   14.129526] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.144619] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   14.179815] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[   14.200855] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
```





```
sudo lshw -C network

[sudo] password for danilo: 
  
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:21:85:47:8f:3b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdfc0000-fdfdffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:1c:3a:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:fdefe000-fdefffff
```




```
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

```




```
uname -mr

2.6.32-21-generic i686
```

---

### Post by danilosoares on 2010-09-03
I have tried to mess with the adapter's power saving settings in Windows, but the problem still persists. This is really kind of frustrating. Could anyone help me out?

---

### Post by danilosoares on 2010-09-06
What am I doing wrong? What should I do to get a response?

---

