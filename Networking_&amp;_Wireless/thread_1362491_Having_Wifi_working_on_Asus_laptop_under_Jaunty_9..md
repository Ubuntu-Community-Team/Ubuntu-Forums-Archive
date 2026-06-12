---
title: "Having Wifi working on Asus laptop under Jaunty 9.04"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by gfombell on 2009-12-23
Hi,

I have installed Ubuntu Jaunty 9.04 on an ASUS laptop and I don't manage to have the wifi working.
[SIZE=3]
[/SIZE][SIZE=3]Symptoms[/SIZE]

[LIST]
[*]Internet is working via Ethernet
[*]Wifi is working with friends' laptops visiting
[*]Wireless network is desactivated on Network Manager Menu
[*]Wireless signal on the laptop is off, when I press Fn+F2 it lights up for a seconde and switch off again. It switches on if I do the command to activate it
[/LIST]
[SIZE=3]Codes[/SIZE]
```
clotilde@Mistouflon-a-cornes:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
clotilde@Mistouflon-a-cornes:~$ lsusb
Bus 001 Device 002: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
clotilde@Mistouflon-a-cornes:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
clotilde@Mistouflon-a-cornes:~$ lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
clotilde@Mistouflon-a-cornes:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:0e:ed:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.20 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:d6:1d:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:5d:e4:b0:fa:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
clotilde@Mistouflon-a-cornes:~$ lsmod
Module                  Size  Used by
rfkill_input           12800  0 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
arc4                    9856  2 
snd_hda_intel         435636  5 
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
b43                   131484  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 b43
pcmcia                 44748  0 
ppdev                  15620  0 
stkwebcam              29188  0 
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             40100  1 
videodev               41600  1 stkwebcam
sdhci_pci              15232  0 
psmouse                61972  0 
cfg80211               38032  1 mac80211
video                  25360  0 
soundcore              15200  1 snd
pcspkr                 10496  0 
parport                42220  3 lp,ppdev,parport_pc
v4l1_compat            21764  1 videodev
sdhci                  23940  1 sdhci_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
asus_laptop            24440  0 
serio_raw              13316  0 
input_polldev          11912  1 b43
output                 11008  1 video
i2c_piix4              18448  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
led_class              12036  2 b43,asus_laptop
shpchp                 40212  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
ssb                    41220  1 b43
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
clotilde@Mistouflon-a-cornes:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

clotilde@Mistouflon-a-cornes:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:0e:ed:b8  
          inet adr:192.168.1.20  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21a:92ff:fe0e:edb8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4890 erreurs:0 :0 overruns:0 frame:0
          TX packets:4566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:5433580 (5.4 MB) Octets transmis:702268 (702.2 KB)
          Interruption:20 Adresse de base:0xb800 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:4 erreurs:0 :0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:240 (240.0 B) Octets transmis:240 (240.0 B)

clotilde@Mistouflon-a-cornes:~$ 
clotilde@Mistouflon-a-cornes:~$ sudo iwlist sca
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

clotilde@Mistouflon-a-cornes:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

clotilde@Mistouflon-a-cornes:~$ uname -r -m 
2.6.28-11-generic i686
clotilde@Mistouflon-a-cornes:~$ 
clotilde@Mistouflon-a-cornes:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback

clotilde@Mistouflon-a-cornes:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:1A:92:0E:ED:B8

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```[SIZE=3]Already tried
[/SIZE]
[SIZE=3][SIZE=1]so many things that, honestly, I forgot some of them. It includes installing the 9.10 karmic but I even lost the ethernet so I went back to jaunty.
I posted a _[COLOR=Blue][thread on the French forum]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3043030#p3043030")[/COLOR]_ but didn't get the final answer...

please , help!
[/SIZE][/SIZE]

---

### Post by gfombell on 2009-12-23
It seems international competition put additional pressure or maybe the good guy read by chance my lattest post, anyway it was solved using this procedure:
[http://wlety.free.fr/forum/viewtopic.php?id=180](http://wlety.free.fr/forum/viewtopic.php?id=180)

---

