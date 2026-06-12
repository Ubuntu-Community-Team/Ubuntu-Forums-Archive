---
title: "problem of wireless connection with an old thinkpad and xterm"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by claudelo on 2010-08-21
Hi,

I've recently installed xubuntu on my old Thinkpad T40. I have currently problems with the xfce and xubuntu sessions, but I manage to do what I really need with the xterm session. However, I have not yet managed to make wireless conections (wired connection is OK). I use wicd-curses. I see the networks, I choose one, it takes a long time saying that it asks for an IP address, and at the end says it is not connected. I do not understand why it does not work, nor what I should do. Below, the results of several commands so as to make my problem clear. 

cat /etc/lsb-release :
DISTRIB_ID=UBUNTU
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

lsusb : 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0000:7777  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(l avant derniere ligne n etait pas là quand je n'avais pas la clé USB)

lspci : 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

lspci -nn | grep -i net :

02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)

sudo lshw -C network :

  *-network:0
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:78:fe:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:11 memory:c0200000-c0200fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:2d:7e:bc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:c0201000-c0201fff ioport:8000(size=64)

lsmod : 

Module                  Size  Used by
nls_iso8859_1           3249  3 
nls_cp437               4919  3 
vfat                    8933  3 
fat                    47767  1 vfat
usb_storage            39425  3 
snd_intel8x0           25588  0 
fbcon                  35102  71 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
tileblit                2031  1 fbcon
snd_pcm_oss            35308  0 
font                    7557  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
bitblit                 4707  1 fbcon
pcmcia                 33024  0 
softcursor              1189  1 bitblit
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
vga16fb                11385  0 
snd_seq_dummy           1338  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26726  0 
radeon                674824  2 
snd_seq_midi            4557  0 
ttm                    49943  1 radeon
snd_rawmidi            19056  1 snd_seq_midi
ipw2100                66395  0 
joydev                  8708  0 
drm_kms_helper         29297  1 radeon
yenta_socket           20408  2 
rsrc_nonstatic         10015  1 yenta_socket
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
libipw                 39896  1 ipw2100
drm                   162377  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
thinkpad_acpi          68083  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
lib80211                5046  1 libipw
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
intel_agp              24119  1 
psmouse                63245  0 
led_class               2864  1 thinkpad_acpi
nsc_ircc               18220  0 
lp                      7028  0 
shpchp                 28820  0 
parport_pc             25962  1 
agpgart                31724  3 ttm,drm,intel_agp
serio_raw               3978  0 
nvram                   6171  1 thinkpad_acpi
snd                    54148  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
irda                  186556  1 nsc_ircc
video                  17375  0 
output                  1871  1 video
parport                32635  3 ppdev,lp,parport_pc
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
crc_ccitt               1339  1 irda
e100                   28211  0 
floppy                 53016  0 
mii                     4381  1 e100

iwconfig : 

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:"hhonors"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig : 

eth0      Link encap:Ethernet  HWaddr 00:0d:60:2d:7e:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:04:23:78:fe:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:11 Adresse de base:0xa000 Mémoire:c0200000-c0200fff 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:24 erreurs:0 :0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1680 (1.6 KB) Octets transmis:1680 (1.6 KB)

sudo iwlist scan : 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CC:FF:97:FC
                    ESSID:"7771 4060"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:18  Signal level:0  Noise level:0
                    Extra: Last beacon: 3420ms ago
          Cell 02 - Address: 00:19:92:00:EB:C2
                    ESSID:"BBHPS_GUEST"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:18  Signal level:0  Noise level:0
                    Extra: Last beacon: 6600ms ago
          Cell 03 - Address: 00:0F:CC:E9:25:44
                    ESSID:"7222 5210"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:25  Signal level:0  Noise level:0
                    Extra: Last beacon: 492ms ago
          Cell 04 - Address: 00:0F:24:83:D9:C0
                    ESSID:"hhonors"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:71  Signal level:0  Noise level:0
                    Extra: Last beacon: 248ms ago
          Cell 05 - Address: 00:21:29:A1:7E:F3
                    ESSID:"ponoproducts"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1100ms ago
          Cell 06 - Address: 00:14:95:1E:73:49
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1780ms ago
          Cell 07 - Address: 00:17:5A:4F:4D:70
                    ESSID:"hhonors"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    Extra: Last beacon: 2508ms ago
          Cell 08 - Address: 00:12:17:71:70:5B
                    ESSID:"fbwireless-g2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:27  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 748ms ago
          Cell 09 - Address: 00:0E:D7:D1:E9:40
                    ESSID:"hhonors"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    Extra: Last beacon: 328ms ago
          Cell 10 - Address: 00:17:5A:5C:B0:00
                    ESSID:"hhonors"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    Extra: Last beacon: 60ms ago
          Cell 11 - Address: 00:24:B2:DE:6D:74
                    ESSID:"Stay the **** Out"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:23  Signal level:0  Noise level:0
                    Extra: Last beacon: 9536ms ago
          Cell 12 - Address: 00:1F:9E:41:E4:20
                    ESSID:"hhonors"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    Extra: Last beacon: 5492ms ago
          Cell 13 - Address: 00:19:92:00:EB:C3
                    ESSID:"BBHPS_PHONE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:23  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3692ms ago
          Cell 14 - Address: 00:1E:2A:78:7A:6C
                    ESSID:"chocolate"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:20  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7980ms ago
          Cell 15 - Address: 00:1C:DF:1D:50:D0
                    ESSID:"TNetwork1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:20  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3880ms ago
          Cell 16 - Address: 00:1C:DF:18:92:EC
                    ESSID:"Sistahs"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:18  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3684ms ago
          Cell 17 - Address: 00:19:92:00:EB:C1
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:20  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4840ms ago

uname -r -m : 

2.6.32-23-generic i686

cat  /etc/network/interfaces :

auto lo
iface lo inet loopback 

nm-tool : 


** (process:2994): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2100
  State:             disconnected
  Default:           no
  HW Address:        00:04:23:78:FE:56

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    hpsetup:         Ad-Hoc, 2E:22:64:D6:EE:73, Freq 2412 MHz, Rate 11 Mb/s, Strength 20
    K Network:       Infra, F8:1E:DF:FE:07:CB, Freq 2417 MHz, Rate 54 Mb/s, Strength 18 WPA2
    K's Guest Network: Infra, FE:1E:DF:FE:07:CB, Freq 2417 MHz, Rate 54 Mb/s, Strength 16 WPA2
    LisaMadiganInternet: Infra, 00:24:C8:65:5E:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 16 WPA WPA2
    hpsetup:         Ad-Hoc, 56:54:BA:B1:A9:C2, Freq 2412 MHz, Rate 11 Mb/s, Strength 25
    Free Public WiFi:Ad-Hoc, 72:9A:F6:51:35:D3, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    hhonors:         Infra, 00:1F:9E:41:E4:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 31
    H&M:             Infra, 00:25:BC:88:D0:43, Freq 2457 MHz, Rate 54 Mb/s, Strength 18 WPA2
    Poon Palace:     Infra, 00:1A:70:51:CF:8A, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    Sistahs:         Infra, 00:1C:DF:18:92:EC, Freq 2412 MHz, Rate 54 Mb/s, Strength 18 WPA
    hhonors:         Infra, 00:17:5A:5C:B3:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 31
    TNetwork1:       Infra, 00:1C:DF:1D:50:D0, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    chocolate:       Infra, 00:1E:2A:78:7A:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    BUILDORDIE-8:    Infra, 00:1E:2A:EE:40:F3, Freq 2412 MHz, Rate 54 Mb/s, Strength 18 WPA WPA2
    BBHPS_PHONE:     Infra, 00:19:92:00:EB:C3, Freq 2412 MHz, Rate 54 Mb/s, Strength 23 WPA
    hhonors:         Infra, 00:17:5A:5C:B0:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    hhonors:         Infra, 00:0E:D7:D1:E9:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    hhonors:         Infra, 00:17:5A:4F:4D:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    Stay the **** Out: Infra, 00:24:B2:DE:6D:74, Freq 2437 MHz, Rate 54 Mb/s, Strength 23 WEP
    fbwireless-g2:   Infra, 00:12:17:71:70:5B, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    BBHPS_GUEST:     Infra, 00:19:92:00:EB:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 18
    hhonors:         Infra, 00:0F:24:83:D9:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 71
    7222 5210 begin_of_the_skype_highlighting              7222 5210      end_of_the_skype_highlighting:       Infra, 00:0F:CC:E9:25:44, Freq 2437 MHz, Rate 11 Mb/s, Strength 25 WEP
    7771 4060 begin_of_the_skype_highlighting              7771 4060      end_of_the_skype_highlighting:       Infra, 00:0F:CC:FF:97:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 18 WEP
    7255 1640 begin_of_the_skype_highlighting              7255 1640      end_of_the_skype_highlighting:       Infra, 00:0F:CC:EA:DC:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    ponoproducts:    Infra, 00:21:29:A1:7E:F3, Freq 2457 MHz, Rate 54 Mb/s, Strength 31 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:0D:60:2D:7E:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


Any idea?

Thanks,

Claude.

---

