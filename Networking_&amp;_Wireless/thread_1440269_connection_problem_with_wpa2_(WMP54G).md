---
title: "connection problem with wpa2 (WMP54G)"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by bog333 on 2010-03-27
Hi,
I have problem to connect in WPA2 with my WMP54G wireless card. I have no problem when I configure my router in WEP mode. My computer is on Ubuntu 9.10 Karmic Koala amd64 (up to date). I know that my router setting is good because I have an other computer with Xubuntu 9.10 and he can connect in WPA2 without problem. In think that the problem is in the drive. Thanks in advance for your help

lspci -nn | grep -i net
```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
04:09.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:8b:5c:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:23 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:40 erreurs:0 :0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:4146 (4.1 KB) Octets transmis:4146 (4.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:8b:dd:69  
          inet adr:192.168.1.104  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::223:4eff:fe8b:dd69/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4759 erreurs:0 :0 overruns:0 frame:0
          TX packets:4041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4449422 (4.4 MB) Octets transmis:684001 (684.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-69-76-54-12-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
```
sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:04:09.0
       logical name: wmaster0
       version: 00
       serial: 00:23:69:76:54:12
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.104 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fdcf0000-fdcf7fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```
lsmod
```
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
usb_storage            66016  1 
binfmt_misc            10220  1 
vboxnetadp             93292  0 
vboxnetflt            100300  0 
vboxdrv              1708492  1 vboxnetflt
snd_hda_codec_analog    79680  1 
snd_usb_audio         102976  1 
snd_usb_lib            19648  1 snd_usb_audio
arc4                    2144  2 
iptable_filter          3872  0 
ecb                     3296  2 
snd_mpu401              9288  0 
snd_mpu401_uart         8480  1 snd_mpu401
snd_seq_dummy           3460  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
ppdev                   8232  0 
gspca_zc3xx            52256  0 
gspca_main             26816  1 gspca_zc3xx
videodev               43360  1 gspca_main
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_seq_oss            33440  0 
psmouse                57124  0 
serio_raw               6596  0 
rt61pci                23556  0 
crc_itu_t               2336  1 rt61pci
rt2x00pci               9216  1 rt61pci
rt2x00lib              34624  2 rt61pci,rt2x00pci
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210008  2 rt2x00pci,rt2x00lib
cfg80211              109144  2 rt2x00lib,mac80211
eeprom_93cx6            2528  1 rt61pci
ns558                   6688  0 
k8temp                  5504  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
i2c_nforce2             8168  0 
nvidia               9630536  40 
snd_seq_midi            8192  0 
snd_rawmidi            27360  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  21 snd_hda_codec_analog,snd_usb_audio,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
gameport               13712  2 ns558
asus_atk0110            9472  0 
parport_pc             37352  1 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
forcedeth              61292  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
floppy                 65192  0
```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:4D:4C:D8   
          Bit Rate=54 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```
uname -r -m
```
2.6.31-17-generic x86_64
```
cat  /etc/network/interfaces
```
auto lo
iface lo inet loopback
```
nm-tool
```
NetworkManager Tool

State: connected

- Device: wlan0  [Auto dd-wrt] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        00:23:4E:8B:DD:69

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Tchoupie:        Infra, 00:13:10:D6:9F:C8, Freq 2437 MHz, Rate 11 Mb/s, Strength 42 WEP
    BELL671:         Infra, 00:26:50:6A:55:01, Freq 2427 MHz, Rate 54 Mb/s, Strength 42 WEP
    Stéphane:       Infra, 00:1C:F0:4D:81:CC, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WPA
    linksys:         Infra, 00:25:9C:4D:4C:A5, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    dlink:           Infra, 00:17:9A:21:F7:78, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    BELL525:         Infra, 00:26:50:E2:E8:29, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WEP
    BELL580:         Infra, 00:24:56:92:C9:A1, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WEP
    Cola's Network:  Infra, 00:23:CD:F0:A1:44, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP
    surfingarea2:    Infra, 00:03:2F:3A:0F:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP
    bonjour toto:    Infra, 00:1B:11:CD:47:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA
    CEMRE O.DMC:     Infra, 00:1B:5B:6D:8E:99, Freq 2457 MHz, Rate 54 Mb/s, Strength 48 WEP
    stef:            Infra, 00:22:B0:BA:51:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA
    *dd-wrt:         Infra, 00:25:9C:4D:4C:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 91 WEP
    BELL995:         Infra, 00:24:56:EF:0F:79, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WEP
    BELL066:         Infra, 00:26:50:B6:4B:31, Freq 2432 MHz, Rate 54 Mb/s, Strength 48 WEP
    Appart Lau et So:Infra, 00:1E:58:3C:B2:77, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    BELL504:         Infra, 00:23:51:96:CB:F9, Freq 2417 MHz, Rate 54 Mb/s, Strength 68 WEP
    Routeur-H:       Infra, 00:21:91:0F:CE:7D, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA
    FuckLesBS:       Infra, 00:18:39:80:4C:47, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:17:31:8B:5C:B3

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

---

