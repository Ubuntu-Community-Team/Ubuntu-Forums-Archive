---
title: "Ubuntu 9.10 D-Link DWA 140 card recognized but impossible to connect"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by yanock on 2010-04-30
hello,

I had some troubles in the past with the wireless that's why i gave up to use ubuntu.
 internal card : atheros AR 5005G.  But I just bought a wireless usb key D-Link (which works fine under windows) because the former does not adequately receive.

So I decided to retry the linux adventure, everything would have gone well since my 2 cards are now recognized (nice work from ubuntu), I caught my usual networks, but the connection is running and after a few minute I see the message "disconnected from the network". I tried on several networks wpa, wep and unprotected network nothing works.

I hope that you were not bored with my story and just ask you for help. Thank you in advance.


cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```lsusb
```
Bus 001 Device 005: ID 13fe:3600 Kingston Technology Company Inc. 
Bus 001 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```lspci

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
```lspci -nn | grep -i net
```
02:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```sudo lshw -C network

```
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: wmaster0
       version: 01
       serial: 00:c0:a8:a8:12:82
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:b1:ad:2b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:a000(size=256) memory:c0216000-c02160ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:24:01:10:6b:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
```lsmod

```
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52544  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_atiixp             15720  2 
snd_atiixp_modem       11940  0 
snd_ac97_codec        101216  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2870sta             488820  0 
arc4                    1660  4 
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
rt2800usb              37372  0 
ip_tables              11692  1 iptable_filter
ecb                     2524  4 
pcmcia                 36808  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00usb              11548  1 rt2800usb
x_tables               16544  1 ip_tables
joydev                 10272  0 
ath5k                 124260  0 
rt2x00lib              29756  2 rt2800usb,rt2x00usb
snd                    59204  15 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24200  1 
input_polldev           3716  1 rt2x00lib
tifm_7xx1               5372  0 
led_class               4096  2 ath5k,rt2x00lib
soundcore               7264  1 snd
rsrc_nonstatic         11644  1 yenta_socket
lp                      8964  0 
mac80211              181236  3 rt2x00usb,ath5k,rt2x00lib
ath                     8060  1 ath5k
psmouse                56180  0 
tifm_core               7832  1 tifm_7xx1
i2c_piix4               9932  0 
snd_page_alloc          9156  3 snd_atiixp,snd_atiixp_modem,snd_pcm
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                35340  2 ppdev,lp
cfg80211               93052  4 ath5k,rt2x00lib,mac80211,ath
k8temp                  4188  0 
serio_raw               5280  0 
shpchp                 32272  0 
crc_ccitt               1852  1 rt2800usb
usbhid                 38208  0 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NEUF_4418"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associ
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"SFR WiFi Public"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associ
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:b1:ad:2b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:23 Adresse de base:0xa000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier
          collisions:0 lg file transmission:0 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:a8:12:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:24:01:10:6b:e6  
          adr inet6: fe80::224:1ff:fe10:6be6/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrie
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:3846 (3.8 K

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-A8-12-82-31-30-
-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-24-01-10-6B-E6-00-00-
-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)
```sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

wmaster1  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:25:15:2C:44:1C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-192 dBm  
                    Encryption key:off
                    ESSID:"NEUF_4418"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000749e88f18f
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 00094E4555465F34343138
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```uname -r -m

2.6.31-14-generic i686


cat  /etc/network/interfaces

auto lo
iface lo inet loopback

nm-tool

```
NetworkManager Tool

State: disconnected

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:24:01:10:6B:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SFR WiFi Public: Infra, 00:17:33:AB:B8:CA, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Neuf WiFi:       Infra, 00:17:33:AB:B8:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    FreeWifi:        Infra, B2:FB:ED:E6:53:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    NEUF_B8C4:       Infra, 00:17:33:AB:B8:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    NEUF_4418:       Infra, 00:25:15:2C:44:1C, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    Livebox-EF1A:    Infra, 00:18:E7:6D:01:F7, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:C0:A8:A8:12:82

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NEUF_4418:       Infra, 00:25:15:2C:44:1C, Freq 2462 MHz, Rate 54 Mb/s, Strength 38
    Livebox-EF1A:    Infra, 00:18:E7:6D:01:F7, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:0A:E4:B1:AD:2B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```P.S. that's a french distribution ;) , yes, I'm french that's why my english isn't very good

---

